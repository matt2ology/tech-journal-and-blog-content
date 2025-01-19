---
authors: Fireship
categories:
date: 2025-01-16
draft: true
source-url: https://www.youtube.com/watch?v=scEDHsr3APg&ab_channel=Fireship
media: articles
notes: reference
tags: readwise, reference/articles, consumed
title: Reference - DevOps CI/CD Explained in 100 Seconds
---

## DevOps CI/CD Explained in 100 Seconds

![rw-book-cover](https://i.ytimg.com/vi/scEDHsr3APg/maxresdefault.jpg)

published-date: 2020-03-12

**Link:** [DevOps CI/CD Explained in 100 Seconds](https://www.youtube.com/watch?v=scEDHsr3APg&ab_channel=Fireship)

## Highlights

### id827894256

> DevOps is a set of practices to build, test, and release your code in small, frequent steps.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrhwm1jk0qq1vtr1q8ex5nq)

### id827894283

> One of the core practices of DevOps is continuous integration, which has developers commit their code to a shared repository often on a daily basis.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrhxae8ahx6p44g5kxtbg6b)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrhxae8ahx6p44g5kxtbg6b)
Continuous Integration is...

### id827894631

> Each commit triggers an automated workflow on a CI server that can notify developers of any issues integrating their changes.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrhz53ehpjvy37ctetjwzzn)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrhz53ehpjvy37ctetjwzzn)
Continuous Integration happens when...

### id827895073

> When a repo evolves in small steps like this, it prevents what’s known as merge towel.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrj018g152bz2v32ehhxt6x)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrj018g152bz2v32ehhxt6x)
Continuous Integration mitigates "merge hell"

### id827896289

> Imagine, Mary, you’re a backend developer building a new API for your product. Shortly after, Jane, your front-end developer, starts work on a new UI. A few months later, when it comes time to merge their features, we find that they’re completely incompatible. The build fails, and we now have to spend a bunch of time and money resolving these conflicts.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrj2g9wrfm7cf4ddb5a0gzs)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrj2g9wrfm7cf4ddb5a0gzs)
A scenario where Continuous Integration using GitHub Actions help alleviate/prevent this issue.

### id827896698

> I need to run three commands: test, build, and deploy. I can automate this entire process in the cloud by using a CI service like GitHub Actions.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrj5ttv6s8ctkkpdr0vr2n5)

### id827896728

> Create a workflow
> \- [(View Highlight)](https://read.readwise.io/read/01jfrj6syb3rxpkktywpkjas4c)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrj6syb3rxpkktywpkjas4c)
Step 01: Create a workflow in your project repository.
`.github/workflows/deploy.yml`

### id827896779

> then I tell it to run on every push to the master branch.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrj8n415gdws2jkk7st5j5t)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrj8n415gdws2jkk7st5j5t)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
  - main
```

### id827896928

> The event triggers a job that runs on a Linux container in the cloud
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjcw7z819m56swnrrs2qwr)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjcw7z819m56swnrrs2qwr)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
  - main
jobs:
build:
runs-on: ubuntu-latest
```

### id827896983

> we tell the container what to do as a series of steps. First, it checks out the code in this GitHub repo
> \- [(View Highlight)](https://read.readwise.io/read/01jfrje6ad1b27ey86sw5fdz7t)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrje6ad1b27ey86sw5fdz7t)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
  - main
jobs:
build:
runs-on: ubuntu-latest
steps:
  - uses: actions/checkout@v2
```

### id827897022

> then sets up Node.js
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjga1k8xjkag5pcka9gyt6)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjga1k8xjkag5pcka9gyt6)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
  - main
jobs:
build:
runs-on: ubuntu-latest
steps:
  - uses: actions/checkout@v2
  - uses: actions/setup-node@v4
with:
node-version: 12
```

### id827897133

> installs my dependencies
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjk7xhy7km95tw98prn0sp)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjk7xhy7km95tw98prn0sp)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
- main
jobs:
build:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v4
with:
node-version: 12
- run: npm ci # this means install
```

### id827897180

> and runs my tests.
> Build and deploy commands.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjmw8jye1jfwz30t2fvd6x)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjmw8jye1jfwz30t2fvd6x)
Step 02: Run on every push to the main branch.
`.github/workflows/deploy.yml`

```yml
name: CI/CD is Easy!
on:
push:
branches:
- main
jobs:
build:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v4
with:
node-version: 12
- run: npm ci # this means install
- run: npm test
- run: npm run build
- run: npm run deploy
```

### id827897754

> Now, anytime we commit code to the master branch in this repo, it will run this workflow. If any of the steps fail, the bad software won't be delivered to our customers, and we will automatically know there's an issue that needs to be addressed.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjrhgppkreanf0rz89adgd)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjrhgppkreanf0rz89adgd)
It can be seen, logged into your account, project repository > Actions

### id827897896

> CI/CD offers two main benefits.
> It helps you automate things that would otherwise have to be done manually by developers, which will increase your velocity, but it also detects small problems early, before they can grow into major disasters, and that results in higher code quality.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrjvsxtyz706vvw46wq2cvy)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrjvsxtyz706vvw46wq2cvy)
The two main benefits are:

1. Helps you automate routines/steps that would have to be done manually by you or other developers; in effect, increases your/team's velocity.
2. Continuous integration detects small problems early before becoming a roadblock; and so, yields higher code quality from all contributors.
