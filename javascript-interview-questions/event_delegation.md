## Event Delegation
- The concept of attaching the events on the parent to handle user events, instead of attaching on each child.
- Useful to reduce memory as less listeners are needed
- Also, children can be removed easily without worrying about memory leak
- For example, in the list, adding new li, it will have the event handler from onClick.

```html
<ul onClick="alert('hi')">
  <li></li>
</ul>
```


### More example
```js
<ul id="parent-list">
	<li id="post-1">Item 1</li>
	<li id="post-2">Item 2</li>
	<li id="post-3">Item 3</li>
	<li id="post-4">Item 4</li>
	<li id="post-5">Item 5</li>
	<li id="post-6">Item 6</li>
</ul>
```

```js
document.getElementById('parent-list'). addEventListener('click', function(e) {
  if (e.target && e.target.nodeName === 'li') {
    console.log("list item ", e.target.id.replace('post-'), " was clicked!");
  }
})
```