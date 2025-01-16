---
authors: Beyond Fireship
categories:
date: 2025-01-16
draft: true
source-url: https://www.youtube.com/watch?v=yfBtjLxn_6k&ab_channel=BeyondFireship
mediums: articles
notes: reference
tags: readwise, reference/articles
title: Reference - How GitHub Actions 10x My Productivity
---
## How GitHub Actions 10x My Productivity

![rw-book-cover](https://i.ytimg.com/vi/yfBtjLxn_6k/maxresdefault.jpg)

published-date: 2023-07-31

**Link:** [How GitHub Actions 10x My Productivity](https://www.youtube.com/watch?v=yfBtjLxn_6k&ab_channel=BeyondFireship)

## Highlights
### id820180151

> one of the secrets to productivity in life is automation as I plow through life I try to delegate anything repetitive to the robot so I can focus on the things that are really important in life
> \- [(View Highlight)](https://read.readwise.io/read/01je7gvmg7xb8w08vragyy9jbt)

### id820180232

> Now with an action you can trigger some code to run automatically when one of these events take place in the background GitHub will spin up a magical Cloud computer also known as a container that's built to your specifications and runs your code to automate things like testing
>   deployment and so on
> \- [(View Highlight)](https://read.readwise.io/read/01je7gz01c0jgqk7g03s4yf6dx)

### id820180284

> GitHub has a generous free tier
> \- [(View Highlight)](https://read.readwise.io/read/01je7h0xbsd166mtwvbj99d1eb)

### id820180372

> to get started just create a hidden GitHub directory in the root of your project followed by a workflows directory then inside of that create a yaml file that can be named whatever you want
> \- [(View Highlight)](https://read.readwise.io/read/01je7h2dtyfksw1afgja8m3jdb)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7h2dtyfksw1afgja8m3jdb)
Example: `.github/workflows/test.yml`

### id820180494

> there's one project that I would highly recommend you install called act this is a CLI tool that will emulate GitHub workflows for you so you can test them locally you'll also need to have Docker installed and running because what it does is build out an actual container just like it does in
>   the cloud with GitHub actions
> \- [(View Highlight)](https://read.readwise.io/read/01je7h6ejejxw781cyx3wettz6)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7h6ejejxw781cyx3wettz6)
- <https://nektosact.com/>
- Prerequisite: [Install Docker Desktop](https://www.docker.com/products/docker-desktop/)

### id820180731

> once you have act installed you can run the ACT command which by default will emulate an on push event to run any workflows that are tied to pushing code to the repo
> \- [(View Highlight)](https://read.readwise.io/read/01je7hdnvwp4c83wncnhswh050)

### id820181722

> first you give the workflow a name just to identify it then most importantly the
>   on property will tell GitHub on which events to run this action in our case we want to test our code whenever we push it to the main or Master Branch however we also want to test code whenever a pull request comes through that's requesting to merge code into the master Branch
> \- [(View Highlight)](https://read.readwise.io/read/01je7hj41e5w442qbh6777d40v)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7hj41e5w442qbh6777d40v)
```yml
name: Run Playwright Tests
on:
push:
branches: [main, master]
pull_request:
branches: [main, master]
```

### id820181906

> we can Define one or more jobs which is the actual code that will run in the cloud give it a name like build and then specify an operating system for it to run on
> \- [(View Highlight)](https://read.readwise.io/read/01je7hqnvfq2dfqh6d1pyhd44g)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7hqnvfq2dfqh6d1pyhd44g)
```yml
name: Run Playwright Tests
on:
push:
branches: [main, master]
pull_request:
branches: [main, master]
jobs:
build:
runs-on: ubuntu-latest
```

### id820182004

> you can also use a matrix strategy to run your jobs in multiple environments like Windows
>   and Linux
> \- [(View Highlight)](https://read.readwise.io/read/01je7hsv65tm6bdpmqwtagcr5k)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7hsv65tm6bdpmqwtagcr5k)
```yml
name: Run Playwright Tests
on:
push:
branches: [main, master]
pull_request:
branches: [main, master]
jobs:
build:
runs-on: ${{ matrix.os }}
```

### id820182381

> every workflow job is broken up into a series of steps and this is the part where we tell the robots how to do the things that we would otherwise have to do manually the first step uses the uses option which is a keyword that allows us to use pre-built steps like checkout will bring the code from the repository into the container and then set up node We'll add node.js and npm to your path I'm also using the width keyword to specify node 18. now that we have an environment set up the way we need it we can use npmci which is the equivalent to
>   npm install but does a clean install which is what you want for automated environments and then when it comes to playwright it recommends using npx instead of your local binaries so we'll go ahead and do that for the install and the testing of playwright
> \- [(View Highlight)](https://read.readwise.io/read/01je7hvppp34esapkdj3tge5qw)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7hvppp34esapkdj3tge5qw)
- The `uses` option is a keyword allows programmers to "use" pre-built steps
- Checkout (`actions/checkout@v2`): brings code from the repository into the container
- Node Setup (`actions/setup-node@v2`): adds Node.js and npm to the path
```yml
name: Run Playwright Tests
on:
push:
branches: [main, master]
pull_request:
branches: [main, master]
jobs:
build:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v2
with:
node-version: 18
- run: npm ci
- run: npx playwright install --with-deps
- run: npx playwright test
```

### id820189132

> when it comes to playwright is that there's another step we can use called upload artifact what this will do is save the playwright report as an artifact in the GitHub actions environment that means if
>   your tests do fail you can go into the artifacts and get a detailed report of what went wrong and then they'll be automatically deleted after 30 days
> \- [(View Highlight)](https://read.readwise.io/read/01je7m3aa8vb0mtrjwn9rfczxr)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01je7m3aa8vb0mtrjwn9rfczxr)
```yml
name: Run Playwright Tests
on:
push:
branches: [main, master]
pull_request:
branches: [main, master]
jobs:
build:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v2
with:
node-version: 18
- run: npm ci
- run: npx playwright install --with-deps
- run: npx playwright test
if: always()
with:
name: playwright-report
path: playwright-report/
retention-days: 30
```



