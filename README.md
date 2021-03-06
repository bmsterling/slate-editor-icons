# slate-editor-icons

> Shared icons and render functions for slate editors, icons are extracted from [Quill editor](https://quilljs.com/) (see [quill-icons](https://github.com/Canner/quill-icons) for more information)

### IMPORTANT NOTE:
`slate-editor-icons` are for managing feature functions and components. If you don't want to assemble editor by yourself you can directly use list below, which use these packages to build editors on top of it:

1. **Another rich text editor using Slate framework, with beautiful design:  https://github.com/Canner/canner-slate-editor**
3. **A markdown editor, that allows you to edit live.: https://github.com/Canner/slate-md-editor**
2. **Quick and customizable way to implement medium like toolbar in your slate editor: https://github.com/Canner/slate-toolbar**

Live demo: https://canner.github.io/slate-editor-icons/

![Demo](https://raw.githubusercontent.com/Canner/slate-editor-icons/master/docs/demo.png)


## Packages

**DON'T DIRECTLY INSTALL `slate-editor-icons`**

Supported features:

- [Align - @canner/slate-icon-align](./packages/slate-icon-align) - center, left, right
- [Blockquote - @canner/slate-icon-blockquote](./packages/slate-icon-blockquote)
- [Bold - @canner/slate-icon-bold](./packages/slate-icon-bold)
- [Clean - @canner/slate-icon-clean](./packages/slate-icon-clean)
- [Code - @canner/slate-icon-code](./packages/slate-icon-code)
- [CodeBlock - @canner/slate-icon-codeblock](./packages/slate-icon-codeblock)
- [Emoji - @canner/slate-icon-emoji](./packages/slate-icon-emoji)
- [Font background color - @canner/slate-icon-fontbgcolor](./packages/slate-icon-fontbgcolor)
- [Font color - @canner/slate-icon-fontcolor](./packages/slate-icon-fontcolor)
- [Hr - @canner/slate-icon-hr](./packages/slate-icon-hr)
- [Header - @canner/slate-icon-header](./packages/slate-icon-header) - header 1, header 2, header 3, header 4, header 5, header 6
- [Image - @canner/slate-icon-image](./packages/slate-icon-image)
- [Indent - @canner/slate-icon-indent](./packages/slate-icon-indent) - indent, outdent
- [Italic - @canner/slate-icon-italic](./packages/slate-icon-italic)
- [Link - @canner/slate-icon-link](./packages/slate-icon-link)
- [List - @canner/slate-icon-list](./packages/slate-icon-list) - Ol list, Ul list
- [Strike through - @canner/slate-icon-strikethrough](./packages/slate-icon-strikethrough)
- [Underline - @canner/slate-icon-underline](./packages/slate-icon-underline)
- [Undo - @canner/slate-icon-undo](./packages/slate-icon-undo)
- [Redo - @canner/slate-icon-redo](./packages/slate-icon-redo)
- [Video - @canner/slate-icon-video](./packages/slate-icon-video)
- [Table - @canner/slate-icon-table](./packages/slate-icon-table)

Supported selectors:

- [Font size - @canner/slate-select-fontsize](./packages/slate-select-fontsize)
- [Line height - @canner/slate-select-lineheight](./packages/slate-select-lineheight)
- [Letter spacing - @canner/slate-letterspacing](./packages/slate-select-letterspacing)

Helpers:

- [Renderers - @canner/slate-editor-renderer](./packages/slate-editor-renderer)
- [Serializer and deserializer - @canner/slate-editor-html](./packages/slate-editor-html)

## Usage

This project is maintain in a monorepo, see packages in `packages` folder

Install icons that you want to support in your slate project, and pass slate editor `change (value.change())` and `onChange` function as props into the component. When users click these icons it will apply changes and trigger onChange function to update new change to your editor.

**NOTE: You have to add corresponding plugins to your editor!**

You will need to pass icon classnames as props into your components ([supported classes](https://github.com/Canner/quill-icons#props)), you could look at the example [how to setup your icon's styles](https://github.com/Canner/slate-editor-icons/blob/master/docs/style.css) 

```js
class App extends React.Component {
  // Set the initial state when the app is first constructed.
  state = {
    value: initialValue // your slate editor's initial value
  }

  render() {
    const {value} = this.state;
    const onChange = ({value}) => this.setState({value});

    return (
      <div style={{margin: '50px'}}>
        <div className="toolbar">
          {icons.map((Type, i) => {
            return <Type
              change={value.change()}
              onChange={onChange}
              key={i}
              className="toolbar-item"
              activeClassName="toolbar-item-active"
              activeStrokeClassName="ql-stroke-active"
              activeFillClassName="ql-fill-active"
              activeThinClassName="ql-thin-active"
              activeEvenClassName="ql-even-active"
            />
          })}
        </div>
        <div className="editor markdown-body">
          <Editor
            value={value}
            onChange={onChange}
            plugins={plugins} // ----> use corresponding plugins of your selected icons, for example `Bold` icon use `BoldPlugin`
          />
        </div>
      </div>
    );
  }
}
```

The best explanation is a simple example: https://github.com/Canner/slate-editor-icons/blob/master/docs/index.js

## Icon and selectors' props

All icons must passed these two props to ensure working properly.

| **props** | **type** | **required** | **default** | **description**  |
|-----------|----------|--------------|-------------|------------------|
| type     | string   | false        | each icons are different  | customized block/mark types |
| change     | object   | true        | null          | changes to value |
| onChange  | func   | true         | null         | onChange function usually `change => this.setState({value})` to update slate state  |


## Start example server

```
npm start
```

## Maintainer

[chilijung](https://github.com/chilijung)

## License

MIT © [Canner](https://github.com/Canner)


<a href="https://canner.io">
  <img src="https://user-images.githubusercontent.com/26116324/37811196-a437d930-2e93-11e8-97d8-0653ace2a46d.png"/>
</a>
