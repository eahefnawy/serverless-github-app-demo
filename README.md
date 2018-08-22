This repository demonstrates how users could use our Serverless Github App in their serverless app repo to receive deployment status on their PRs.

## Setup
1. Install Travis into your repo by [clicking here](https://github.com/marketplace/travis-ci).
2. Configure Travis to deploy your app to the Serverless Platform by exporting the access key to the Travis env.
3. Install Serverless Github App into your repo by [clicking here](https://github.com/apps/serverless-platform)
4. Make any changes, then submit a PR. As Travis deploys your application, you'll see real time deployment status updates from the Serverless Github App. [Here's an example PR](https://github.com/eahefnawy/serverless-github-app-demo/pull/1)

## How It Works
The Serverless Github App only requires permission to read/write statuses on your selected repos. During deployment, the platform sdk will detect that it's running in Travis environment, and provide extra data to the Serverless Platform (like commit sha, repo, owner...etc) so that it could create a status.

The platform-sdk currently have built-in support only for Travis, so all you need to do is install the Serverless Github App, and export your access key to Travis. If you are using another CI system, you'll need to export the following env vars manually:

```
CI=true
CI_SOURCE_OWNER # ie. serverless
CI_SOURCE_REPO # ie. service-name
CI_SOURCE_TYPE # ie. github
CI_COMMIT # ie. wertyuio
CI_TYPE # ie. Jenkins
CI_BUILD_ID # ie. 123456789
```

## Next Steps
This is our first iteration for a Github App, and I think it can give us great power to offer more value. Here are some ideas:

- We can provide more data about the deployment using the CheckRun API. Users will be able to see this data in the "Checks" tab.
- With read access to repos, we can provide a Serverless CD solution for users so that they don't have to depend on Travis. A lot like how it works with Netlify.
- With read access to repos, we can validate serverless.yml and make auto generated comments on the codebase.
- Many others!