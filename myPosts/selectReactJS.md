<img href='http://www.toptal.com/uploads/blog/category/logo/291/react.png'/>
Forms in React can be a little tricky. To effectively gather the values out of our forms, we need them to be controlled components. The following is the <a href='http://facebook.github.io/react/docs/forms.html'>example</a> is given by in the React Documentation for an input:

```
var InputComponent = React.createClass({
  getInitialState: function() {
      return {value: 'Hello!'};
    },
    handleChange: function(event) {
      this.setState({value: event.target.value});
    },
    render: function() {
      var value = this.state.value;
      return <input type="text" value={value} onChange={this.handleChange} />;
    }
});

```

When the user types something into this component, the onChange event is triggered, setState is called, and React will dynamically re-render the component. This seems like a lot of work for one component, but having controlled components is best way to integrate user interactions with the rest of our application. If this input has a parent component which needs access to the data provided by the user, we can extract that data via the the input's state.

The following is an example of how we would implement a controlled Select element in React:

```
var options = ['Ferrari', 'Lamborghini', 'Mazeratti', '1989 Mazda MPV'];

var SelectComponent = React.createClass({
  getInitialState: function(){
    return {
      selectValue: this.props.options[0]
    };
  },
  handleChange: function(e){
    var selectedOption = e.target.value;
    this.setState({
      selectValue: selectedOption
    });
  },
  render: function(){
    var selectValue = this.state.selectValue;
    var cOptions = this.props.options.map(function(item, index){
      return <option key={index} value={item}>{item}</option>
    });
    return (
      <div>
        <select onChange={this.handleChange} value={selectValue}>{cOptions}</select>
      </div>
    )
  }
});

React.render(<SelectComponent options={options}/>, document.body);
```

The following will render a controlled select component, that updates its state when a user selects a different object.