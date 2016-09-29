---
layout:     guidelines
title:      "React/JSX Style Guide"
subtitle:   "A mostly reasonable approach to React and JSX"
collection: guidelines
---

## Table of Contents
{:.no_toc}

1. Automatic Table of Contents Here
{:toc}

## Props

Always use camelCase for prop names.

```
// bad
<Foo
  UserName="hello"
  phone_number={12345678}
/>

// good
<Foo
  userName="hello"
  phoneNumber={12345678}
/>
```

Omit the value of the prop when it is explicitly `true`. [^jsx-boolean-value]

```
// bad
<Foo
  hidden={true}
/>

// good
<Foo
  hidden
/>
```

[^jsx-boolean-value]: [ESLint: react/jsx-boolean-value](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-boolean-value.md)

Avoid using an array index as `key` prop, prefer a unique ID: using the index as a key is an [anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318).

```
// bad
{todos.map((todo, index) =>
  <Todo
    {...todo}
    key={index}
  />
)}

// good
{todos.map(todo => (
  <Todo
    {...todo}
    key={todo.id}
  />
))}
```

## Tags

Always self-close tags that have no children. eslint: [`react/self-closing-comp`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/self-closing-comp.md)

```
// bad
<Foo className="stuff"></Foo>

// good
<Foo className="stuff" />
```

If your component has multi-line properties, close its tag on a new line. eslint: [`react/jsx-closing-bracket-location`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-closing-bracket-location.md)

> Why? It produces nicer diffs.

```
// bad
<Foo
  bar="bar"
  baz="baz" />

// good
<Foo
  bar="bar"
  baz="baz"
/>
```
