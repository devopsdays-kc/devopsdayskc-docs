# Documentation for DevOpsDays KC

This website is built using [Docusaurus 2](https://docusaurus.io/), a modern static website generator. The following steps are what is necessary to begin to contribute to the documentation.

## Contributing

We welcome any and all contributions to the documentation. In order to do so, you'll need to setup a local environment first.

### Setup your local copy

#### Fork the repo and install dependencies

1. Fork the repo to your GitHub org, and then clone it to your local machine:

```
git clone https://github.com/<GITHUB_USER>/docs.git
```

2. Install dependencies

```
cd docs
npm install
```

3. Kick off the local development server to reflect live most changes you make.

```
npm start
```

#### Local Development and testing

If you have your local development server already started, you're ready to start reflecting your changes. If not, run `npm start` from your repo folder.

Before you are ready to push your changes, verify they build and then display correctly by running:

```
npm build ; npm serve
```

This will generate the static content into the `build` directory and then run the local serve against that directory to mirror what will/should be displayed when the changes are deployed.

### Adding new documents

Documents are groups of pages connected through:

- a **sidebar**
- **previous/next navigation**

#### Create your first Doc

Create a Markdown file at `docs/hello.md`:

```md title="docs/hello.md"
# Hello

This is my **first Docusaurus document**!
```

A new document is now available at [http://localhost:3000/docs/hello](http://localhost:3000/docs/hello).

#### Configure the Sidebar

Docusaurus automatically **creates a sidebar** from the `docs` folder.

Add metadata to customize the sidebar label and position:

```md title="docs/hello.md" {1-4}
---
sidebar_label: 'Hi!'
sidebar_position: 3
---

# Hello

This is my **first Docusaurus document**!
```

By default, Docusaurus orders sidebar items by the title of their filename, unless you specify a specific `sidebar_position:`. This will also place individual docs ahead of categories/folders. If it's important that the document be at a specific position, you will need to adjust the `sidebar_position: 3` to fit in amongst the existing docs. If there are two in position "3", it will be sorted by filename, so you may need to adjust the positions for the rest of the docs. 

#### Markdown features

##### Front Matter

Markdown documents have metadata at the top called [Front Matter](https://jekyllrb.com/docs/front-matter/):

```text title="my-doc.md"
// highlight-start
---
id: my-doc-id
title: My document title
description: My document description
slug: /my-custom-url
---
// highlight-end

##### Markdown heading

Markdown text with [links](./hello.md)
```

By default, the link for the doc will be the filename without the `.md` extension. If you want it to be a specific name, then adjust the `slug:` parameter in the front matter accordingly, keeping in mind the folder structure.

You can also control the way the title of the page is displayed in the browser tab bar as well as the sidebar with the `title:` parameter.

##### Links

Regular Markdown links are supported, using url paths or relative file paths.

```md
Let's see how to [Create a page](/create-a-page).
```

```md
Let's see how to [Create a page](./create-a-page.md).
```

**Result:** Let's see how to [Create a page](./create-a-page.md).

##### Images

Regular Markdown images are supported.

You can use absolute paths to reference images in the static directory (`static/img/docusaurus.png`):

```md
![Docusaurus logo](/img/docusaurus.png)
```

![Docusaurus logo](/img/docusaurus.png)

You can reference images relative to the current file as well. This is particularly useful to colocate images close to the Markdown files using them:

```md
![Docusaurus logo](./img/docusaurus.png)
```

##### Code Blocks

Markdown code blocks are supported with Syntax highlighting.

    ```jsx title="src/components/HelloDocusaurus.js"
    function HelloDocusaurus() {
        return (
            <h1>Hello, Docusaurus!</h1>
        )
    }
    ```

```jsx title="src/components/HelloDocusaurus.js"
function HelloDocusaurus() {
  return <h1>Hello, Docusaurus!</h1>;
}
```

##### Admonitions

Docusaurus has a special syntax to create admonitions and callouts:

    :::tip My tip

    Use this awesome feature option

    :::

    :::danger Take care

    This action is dangerous

    :::

:::tip My tip

Use this awesome feature option

:::

:::danger Take care

This action is dangerous

:::

##### MDX and React Components

[MDX](https://mdxjs.com/) can make your documentation more **interactive** and allows using any **React components inside Markdown**:

```jsx
export const Highlight = ({children, color}) => (
  <span
    style={{
      backgroundColor: color,
      borderRadius: '20px',
      color: '#fff',
      padding: '10px',
      cursor: 'pointer',
    }}
    onClick={() => {
      alert(`You clicked the color ${color} with label ${children}`)
    }}>
    {children}
  </span>
);

This is <Highlight color="#25c2a0">Docusaurus green</Highlight> !

This is <Highlight color="#1877F2">Facebook blue</Highlight> !
```

export const Highlight = ({children, color}) => (
  <span
    style={{
      backgroundColor: color,
      borderRadius: '20px',
      color: '#fff',
      padding: '10px',
      cursor: 'pointer',
    }}
    onClick={() => {
      alert(`You clicked the color ${color} with label ${children}`);
    }}>
    {children}
  </span>
);

This is <Highlight color="#25c2a0">Docusaurus green</Highlight> !

This is <Highlight color="#1877F2">Facebook blue</Highlight> !

