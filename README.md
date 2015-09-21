# debounce-collect

An implementation of debounce. Unlike [underscore]'s debounce, this one
collects arguments of all calls.

[underscore]: http://underscorejs.org/

<br>

## Usage

```js
debounce(function, wait, [immediate])
```

Creates and returns a new debounced version of the passed function which will
postpone its execution until after `wait` milliseconds have elapsed since the
last time it was invoked. Useful for implementing behavior that should only
happen after the input has stopped arriving. For example: rendering a preview
of a Markdown comment, recalculating a layout after the window has stopped
being resized, and so on.

Pass *true* for the `immediate` argument to cause `debounce()` to trigger the function
on the leading instead of the trailing edge of the `wait` interval. Useful in
circumstances like preventing accidental double-clicks on a "submit" button
from firing a second time. 

### Differences from `_.debounce`

The resulting function will be called with an array of all function arguments
for all calls.

<br>

## Example

```js
// this will call the update function:
//
//    update('change', 'file1.txt')
//    update('change', 'file2.txt')
//
chokidar.watch('.')
  .on('all', debounce(update, 50))

function update (argsList) {
  console.log(argsList)

  // result:
  // [
  //   [ 'change', 'file1.txt' ],
  //   [ 'change', 'file1.txt' ]
  // ]
}
```

## Thanks

**debounce-collect** © 2015+, Rico Sta. Cruz. Released under the [MIT] License.<br>
Authored and maintained by Rico Sta. Cruz with help from contributors ([list][contributors]).

> [ricostacruz.com](http://ricostacruz.com) &nbsp;&middot;&nbsp;
> GitHub [@rstacruz](https://github.com/rstacruz) &nbsp;&middot;&nbsp;
> Twitter [@rstacruz](https://twitter.com/rstacruz)

[MIT]: http://mit-license.org/
[contributors]: http://github.com/rstacruz/debounce-collect/contributors