# `.dive([options]) => ShallowWrapper`

Shallow render the one non-DOM child of the current wrapper, and return a wrapper around the result.

NOTE: can only be called on wrapper of a single non-DOM component element node.


#### Arguments

1. `options` (`Object` [optional]):
- `options.context`: (`Object` [optional]): Context to be passed into the component



#### Returns

`ShallowWrapper`: A new wrapper that wraps the current node after it's been shallow rendered.



#### Examples

```jsx
function Bar() {
  return (
    <div>
      <div className="in-bar" />
    </div>
  );
}
```

```jsx
function Foo() {
  return (
    <div>
      <Bar />
    </div>
  );
}
```

```jsx
const wrapper = shallow(<Foo />);
expect(wrapper.find('.in-bar')).to.have.lengthOf(0);
expect(wrapper.find(Bar)).to.have.lengthOf(1);
expect(wrapper.find(Bar).dive().find('.in-bar')).to.have.lengthOf(1);
```
