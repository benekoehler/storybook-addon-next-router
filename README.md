# Storybook Addon Next Router

Use Next.js Router in your Storybook stories.

## As a decorator in a story

```jsx
import { withNextRouter } from 'storybook-addon-apollo-client';
import MyComponentThatHasANextLink from '../component-that-has-a-next-link';

export default {
  title: 'My Story',
  decorators: [withNextRouter],
};

// if you have the actions addon
// you can click the links and see the route change events there
export const example = () => <MyComponentThatHasANextLink />;

example.story = {
  parameters: {
    nextRouter: {
      path: '/profile/[id]',
      asPath: '/profile/lifeiscontent',
      query: {
        id: 'lifeiscontent',
      },
    },
  },
};
```

## Usage in `preview.js`

```js
import { withNextRouter } from 'storybook-addon-apollo-client';
import { addDecorator } from '@storybook/react';

addDecorator(
  withNextRouter({
    path: '/' // defaults to `/`
    asPath: '/' // defaults to `/`
    query: {}, // defaults to `{}`
    push() {} // defaults to using addon actions integration, can override any method in the router
  })
);
```

if you set up `withNextRouter` in preview, it will not need to be added to the `decorators` key in each story, consider doing this if you have a lot of stories that depend on Apollo.

Read more about the options available for next/router at https://nextjs.org/docs/api-reference/next/router