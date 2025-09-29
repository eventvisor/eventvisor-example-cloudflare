# eventvisor-example-cloudflare

Example Eventvisor project using [Cloudflare Pages](https://pages.cloudflare.com/).

For more information, visit https://eventvisor.org.

## Accessing datafiles

The generated datafiles from this repository is accessible via these URLs:

- https://eventvisor-example-cloudflare.pages.dev/eventvisor-tag-web.json

### Usage with Eventvisor SDK

Install the SDK in your application:

```
$ npm install --save @eventvisor/sdk
```

Then use it in your application:

```js
import { createInstance } from "@eventvisor/sdk";

const DATAFILE_URL =
  "https://eventvisor-example-cloudflare.pages.dev/eventvisor-tag-web.json";

const datafileContent = await fetch(DATAFILE_URL).then((res) => res.json());

const eventvisor = createInstance({
  datafile: datafileContent,
});
```

Learn more about [SDK usage here](https://eventvisor.org/docs/sdks/javascript/).

## Installation

Since this example app lives outside of the Eventvisor [monorepo](https://github.com/eventvisor/eventvisor), you are recommended to make sure [`package.json`](./package.json) has the latest version of [`@eventvisor/cli`](https://www.npmjs.com/package/@eventvisor/cli) package.

```
$ npm ci
```

## Usage

### Lint

```
$ npx eventvisor lint
```

### Build datafiles

```
$ npx eventvisor build
```

Checkout output in `datafiles` directory.

### Test

```
$ npx eventvisor test
```

## Cloudflare

For this example, we are going to be uploading to and serving our datafiles from [Cloudflare Pages](https://pages.cloudflare.com/).

Make sure you already have a Cloudflare Pages project set up, and then use it in the [`publish`](./.github/workflows/publish.yml) workflow.

## GitHub Actions

This example project is configured to run its CI/CD pipeline with [GitHub Actions](https://github.com/features/actions).

You are free to choose any other CI/CD provider of your choice.

### Settings

Make sure you have `Read and write permissions` enabled in your GitHub repository's `Settings > Actions > General > Workflow permissions` section.

### Workflows

You can find the GHA workflow files in [`.github/workflows`](./.github/workflows) directory.

- `checks` workflow: runs against non-`master` (non-`main`) branches
- `publish` workflow: runs against `master` (`main`) branch

### Secrets

Follow the guide [here](https://developers.cloudflare.com/pages/how-to/use-direct-upload-with-continuous-integration/), and set up these two secrets in your GitHub repository's `Settings > Secrects and variables > Actions` section:

- `CLOUDFLARE_ACCOUNT_ID`
- `CLOUDFLARE_API_TOKEN`
