---
authors: Fireship
categories:
date: 2024-12-23
draft: true
source-url: https://www.youtube.com/watch?v=eB0nUzAI7M8
mediums: articles
notes: reference
tags: readwise, reference/articles, consumed
title: Reference - 5 Ways to DevOps-ify Your App - Github Actions Tutorial
---
## 5 Ways to DevOps-ify Your App - Github Actions Tutorial

![rw-book-cover](https://i.ytimg.com/vi/eB0nUzAI7M8/maxresdefault.jpg)

published-date: 2020-03-16

**Link:** [5 Ways to DevOps-ify Your App - Github Actions Tutorial](https://www.youtube.com/watch?v=eB0nUzAI7M8)

## Highlights
### id827711711

> One of the best ways to increase productivity in a software project is to automate anything manual or repetitive
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy2491p8vm6cxxnfngpn5m)

### id827712002

> five different techniques that can improve the quality of your code and make your life more productive through the magic of DevOps
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy2ttv1a0qrawkc1k8e4zx)

### id827712879

> If you have no idea what terms like continuous integration and delivery mean, you will by the end of this video.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy3thfv3v8kg9y0pmb78yg)

### id827713034

> what GitHub Actions are. Consider a repo on GitHub. There are all kinds of different events that can happen to that repo. Someone might start the repo, send a pull request, or you might merge code into the master branch.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy5y0y3n1qb44g571r47r2)

### id827713058

> These are examples of events, and any event can trigger an automated workflow.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy6999mvhcntkvg9frtcrp)

### id827713120

> A workflow can spin up one or more containers for you in the cloud. Then, you provide a set of steps or instructions for the container to do something useful for you.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy77pwfyz5ef00zjsrz4fb)

### id827713139

> GitHub will log the progress of each step and make it very clear if something failed.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy7m5dt1c1rnmx97sv0979)

### id827713145

> You can think of each step as a reusable chunk of code, which we call an action.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy85bey64wxjt8msnn8ktp)

### id827713311

> A good starting place is continuous integration.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqy8y8rbmnvkny92pk4jtbb)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqy8y8rbmnvkny92pk4jtbb)
What is continuous integration (CI) [DevOps CI/CD Explained in 100 Seconds](https://www.youtube.com/watch?v=scEDHsr3APg&ab_channel=Fireship)

### id827713967

> The whole idea behind continuous integration or CI is to have developers submit their code to the main codebase in small maintainable chunks, usually on a daily basis.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqybytb35wjh1xwr59r4tsc)

### id827714179

> Those changes should be automatically tested against the main codebase.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqycbw0pj7ybsdjac537hhn)

### id827714478

> When you visit your code on GitHub, you'll notice this actions tab. This is where you can monitor your workflows.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqyh6z8ydm5c40t7hwt2r4k)

### id827714515

> When a workflow is triggered, it will Give you a log of everything that happened on the server.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqyhfa0wk9ves40z9nd5d92)

### id827714541

> What we want to do for continuous integration is have our test suite run anytime there's a pull request to the master branch. If the test suite fails or if the code fails to build, we should get a red checkmark here, automatically telling us not to merge
>   that pull request. But if everything goes according to plan, we should get a green checkmark.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqyjd774x596f1wyz2qaqj4)

### id827716423

> in the source code, you can see I have a GitHub directory followed by workflows and a file called integrate.yaml. Anything in this workflows directory will be picked up by GitHub and automatically set up as a workflow in the cloud.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqym05k9y7xqcf455meaqb8)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqym05k9y7xqcf455meaqb8)
>`./.github/workflows/integrate.yml`

### id827721973

> The YAML file is where we define the workflow. We'll give it a name of "Node Continuous Integration." Then we need to tell it on which event or events to run. We do that with the on object, and in this case, we want to run it on pull requests to the master branch.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqyqh8chqwz9d9fzt657d5j)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqyqh8chqwz9d9fzt657d5j)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
```

### id827727986

> Now, every workflow should have one or more jobs. You define them on this jobs object
> \- [(View Highlight)](https://read.readwise.io/read/01jfqytxk6f46aqqcznt8kk28f)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqytxk6f46aqqcznt8kk28f)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
jobs:
```

### id827732296

> give the job a name. We'll call this one "Test Pull Request." From there, we need to tell the job which VM to run on. I'll run this one on Ubuntu, but you also have the choice In Windows and Mac OS
> \- [(View Highlight)](https://read.readwise.io/read/01jfqywxbkwjvsd3bkhwzte20y)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqywxbkwjvsd3bkhwzte20y)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
jobs:
test_pull_request:
runs-on: ubuntu-latest
```

### id827735792

> next we need to give this job a set of steps or instructions that actually build and test our code. First, we want to get our source code into the virtual machine. We can do that using an officially maintained action called checkout that brings your source code into the current
>   working directory, and that means you can run commands like you would from the command line if working on the project locally. But in our case, we also need to set up Node.js in order to run those commands, so we use the Node setup action and then specify the version.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqyyyt41n4g7vmmbddxawq9)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqyyyt41n4g7vmmbddxawq9)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
jobs:
test_pull_request:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v1
with:
node-version: 12
```

### id827747822

> From there, we're ready to start running our own commands. First, we need to install all of our dependencies from NPM, and we can do that using the CI command, which is equivalent to NPM install, but it does a clean install for your CI server.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqz5yc7s0xkvxrwqa6cjmew)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqz5yc7s0xkvxrwqa6cjmew)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
jobs:
test_pull_request:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v1
with:
node-version: 12
- run: npm ci
```

### id827749975

> From there, we'll run our test command to test our code, and then after that, we'll run our build command to make sure the build compiles properly.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqz80t9756bs1dxpy2hk91k)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqz80t9756bs1dxpy2hk91k)
>`./.github/workflows/integrate.yml`
```yml
name: Node Continuous Integration
on:
pull_requests:
branches: [ master ]
jobs:
test_pull_request:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v2
- uses: actions/setup-node@v1
with:
node-version: 12
- run: npm ci
- run: npm test
- run: npm build
```

### id827750057

> to start using it. We just need to commit it to the master branch. I'll run git add, git commit, and then git push to push that to the remote repository.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzaspeftsvwjb1r5fvm5tf)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqzaspeftsvwjb1r5fvm5tf)
```sh
git add .github/workflows/integrate.yml
git commit -m "Adding integration steps for GitHub Actions"
```

### id827750535

> if you go to the actions tab on GitHub, you'll notice that it's still empty. That's because we haven't had an actual pull request event to trigger a workflow.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzeep633vfremvb051nbam)

### id827750671

> by creating a pull request. I'll go ahead and create a new branch using git checkout with the -b flag to automatically move into it.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzg9qb4dwwgk11ghbgr1xp)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqzg9qb4dwwgk11ghbgr1xp)
```sh
git checkout -b testing
```
> `Switched to a new branch 'testing'`

### id827751900

> Inside that branch, I'll make some changes to the source code that cause the test to fail. I'll then commit those changes and push this branch to the remote repo.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzjes3mt4nb3s7g5c29v4y)

### id827752137

> GitHub, I'll see the option to create a pull request, which I'll go ahead and do. You'll notice that it indicates how we're running checks or a
>   continuous integration test in the background.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzk27mjh7w5b1h8f3nweqm)

### id827753884

> In this case, the tests on the pull request fail, which This means we probably shouldn't integrate this code into the main codebase.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzmtwywt9z45ndvkz9r0qs)

### id827754125

> I can look at the logs and realize what I did wrong in this case.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqznsczj8p3d92mmgksr355)

### id827754134

> Since I have an open pull request, I can go back into my code, fix it, and then push another commit to this branch.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzp7bz6fe85n2cx9m952t9)

### id827754155

> ime around, we get green checkmarks. So, that takes care of our continuous integration.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzpyhrncp2stn3bdfgm80t)

### id827754506

> the next phase: continuous deployment.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzqtt79qrnfgppqndn39fd)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqzqtt79qrnfgppqndn39fd)
Phase 02: Continuous Deployment

### id827755020

> continuous integration is about merging new code into the codebase
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzscwc6fq655pyszd7nq5x)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqzscwc6fq655pyszd7nq5x)
The essence of "continuous integration"

### id827755559

> continuous deployment is about pushing that code out to your customers
> \- [(View Highlight)](https://read.readwise.io/read/01jfqztqq2dwcmhxmqawdy56s0)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqztqq2dwcmhxmqawdy56s0)
Essence of "continuous deployment"

### id827756318

> To demonstrate this, I'm going to integrate a third-party host, Firebase, and I'd like to give a shout out to Mark Stammer and Johan; they put together an awesome guide that will take you through each one of these steps.
> \- [(View Highlight)](https://read.readwise.io/read/01jfqzxgt5mayw4a8e0jy7geqz)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfqzxgt5mayw4a8e0jy7geqz)
Marc Stammerjohann's blog post [GitHub Action deploying Angular App to Firebase Hosting](https://fireship.io/snippets/github-actions-deploy-angular-to-firebase-hosting/)

### id827757911

> We can easily set up hosting locally.
>   By running firebase init hosting, then we can push our code to our Firebase hosting account using firebase deploy.
> \- [(View Highlight)](https://read.readwise.io/read/01jfr00pf4gxphs9bndb3pht8c)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfr00pf4gxphs9bndb3pht8c)
```sh
firebase init
firebase deploy --only hosting
```

### id827758304

> We can do all this locally because we're authenticated into our Firebase account on our local system
> \- [(View Highlight)](https://read.readwise.io/read/01jfr05h8jb81b7htqde2pf2jf)

### id827758314

> how do we authenticate a remote CI server to do the same thing? What we'll need to do is share a secret token with GitHub. We can obtain that token from Firebase by running firebase login. This will return us a token string which you can think of as an API key or user name/password combination. Make sure to keep this value secret.
> \- [(View Highlight)](https://read.readwise.io/read/01jfr0604a5npsgvtsmjh9h80v)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfr0604a5npsgvtsmjh9h80v)
```sh
firebase login:ci
```
> `Success! Use this token to login on a CI Server:`
>
> YOUR TOKEN HERE
>
> `Example: firebase deploy --token "$FIREBASE_TOKEN"
```

### id827759847

> copy the value from the command line and then head over to your GitHub repo. Go to Settings and Secrets and add a new secret. We'll give it a name of Firebase token in all caps, and you'll want to make sure to use that same name. Then we'll paste in the token and save it.
> \- [(View Highlight)](https://read.readwise.io/read/01jfr0bwzjtwt8zqm59kkd64zy)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfr0bwzjtwt8zqm59kkd64zy)
Project repository > Settings > Secrets > add name (e.g. "FIREBASE_TOKEN" - it must be in all caps) > in the value text field past your token you copied from the command line > add/save the secret

### id827845458

> GitHub will automatically encrypt this value for us, and then we can access it securely from our CI server. In other words, it gives us a way to securely authenticate with Firebase from a GitHub Actions workflow.
> \- [(View Highlight)](https://read.readwise.io/read/01jframvexdx04t19f43mr595y)

### id827845525

> another YAML file in the workflows directory. This one we'll call It deploys instead of running this workflow on a pull request; we'll run it on a push to the master branch. So this workflow will run if we push code directly to the master branch or if we merge a pull request into it.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrapfc6a2k1azey8adzw30m)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrapfc6a2k1azey8adzw30m)
```yml
name: Firebase Continuous Deployment
on:
push:
branches: [ master ]
```

### id827845621

> the job itself looks almost identical to the previous job. We check out the code, set up Node, run our build command, but then we need to deploy it. To do that, we're going to use a third-party action called the Firebase action.
> \- [(View Highlight)](https://read.readwise.io/read/01jfraryfcp9ykpzzhhzr93fe5)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfraryfcp9ykpzzhhzr93fe5)
```yml
name: Firebase Continuous Deployment
on:
push:
branches: [ master ]
jobs:
deploy:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@master
with:
node-version: 12
- run: npm ci
- run: npm run build
- uses: w9jds/firebase-action@master
```

### id827846070

> This action takes care of all the steps required to set up the Firebase CLI on your server. It will run the Firebase command, and then we tell it to use the arguments of deploy
>   only hosting, and it’s going to be looking for an environment variable of Firebase token. We can access our secret GitHub value by using dollar sign double braces followed by Secrets dot firebase token, and that’s basically all there is to it.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrb1rvrk8vjzegz87y54a0j)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrb1rvrk8vjzegz87y54a0j)
```yml
name: Firebase Continuous Deployment
on:
push:
branches: [ master ]
jobs:
deploy:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@master
with:
node-version: 12
- run: npm ci
- run: npm run build
- uses: w9jds/firebase-action@master
with:
args: deploy --only hosting
env:
FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
```

### id827848920

> We can start using this continuous deployment workflow by pushing it to the master branch.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrb5wryk4915ped1tmw1wxf)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrb5wryk4915ped1tmw1wxf)
```sh
git add .github/workflows/deploy.yml
git commit -m "Added Continuous Deployment workflow"
```

### id827850815

> Now, if we go back to GitHub and merge that pull request from the previous example, you can see from the log that it automatically builds and deploys our code to Firebase, and the changes should be automatically Reflected on the website itself, and now that we have a basic CI/CD pipeline
> \- [(View Highlight)](https://read.readwise.io/read/01jfrbhk25gae4daq9za17eg9p)

### id827851081

> Personally, I maintain a few open-source projects that are available as libraries through NPM.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrbjewyhk8nwpch237kqb49)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrbjewyhk8nwpch237kqb49)
Topic #03: Publish NPM Packages

### id827851657

> One of those projects is spelled fire
> \- [(View Highlight)](https://read.readwise.io/read/01jfrbn3j5wkbhwhjfbqep0fk3)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrbn3j5wkbhwhjfbqep0fk3)
Jeff Delaney, the man behind the YouTube channel Fireship, maintains a "minimal, yet powerful library that puts realtime Firebase data into Svelte stores".
[SvelteFire](https://github.com/codediodeio/sveltefire)

### id827851897

> In this workflow, you'll notice I'm using the release event. That's because not every code change on the master branch is a new release. For example, if you just fix a typo in the README, it doesn't require a whole new release to be pushed out to NPM.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrbv8ggjxzp14fjm2n9zkc1)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrbv8ggjxzp14fjm2n9zkc1)
```yml
name: Sveltefire Package
on:
release:
types: [ created ]
```

### id827851960

> you'll notice we have two jobs: one for build and one to publish to NPM. We might want an additional job to publish to the GitHub package registry. By default, all the jobs will run concurrently in parallel, but that's not actually what we want here.
>   Because we want to first build our code before releasing it to the package managers, we can use the needs keyword to tell GitHub Actions to run this job after the previous job is finished. This can be a really useful technique because in our case here, it allows us to build the code once and then push it out to two different registries without having to rebuild the code. So that's really useful if you're a library maintainer.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrbxn1vazr6fk0bnyfjc9y2)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrbxn1vazr6fk0bnyfjc9y2)
```yml
name: Sveltefire Package
on:
release:
types: [ created ]
jobs:
build:
publish-npm:
needs: build
publish-gpr:
needs: build
```

### id827852327

> most companies use a lot of other communication tools beyond GitHub like Slack, Discord, JIRA, Trello, and so on.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc2718ycnknek3n02wkb71)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrc2718ycnknek3n02wkb71)
Topic #04: Integrate Apps

### id827852599

> GitHub Marketplace, you'll notice that it's separated by apps and actions.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc41h55d064kj168ddq0cq)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrc41h55d064kj168ddq0cq)
In the GitHub Marketplace there is a delineation between "apps" and "actions"

### id827852686

> Actions are reusable pieces of code you use in your own workflow
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc5eshczbzjx4pamqa5h67)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrc5eshczbzjx4pamqa5h67)
An "action" is defined as...

### id827852705

> apps are fully pre-built solutions that don't require you to deploy any code whatsoever.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc6asj988247r5sgjfv6tf)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrc6asj988247r5sgjfv6tf)
In the GitHub Marketplace "apps" are...

### id827852889

> The nice thing about a GitHub app is that it can be used across multiple repos simultaneously.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc8pkz6jdgfyb2965q2rte)

### id827852906

> when you're automating with GitHub Actions, it's a good idea to ask yourself if you want a fully installed app or if you want to build your own workflow with actions.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrc94zeb4v0reag291vats5)

### id827853508

> automatically analyze code quality
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcm5ydvcjct3vpdf72tbyq)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrcm5ydvcjct3vpdf72tbyq)
GitHub Marketplace app: "Codacy"
"Codacy helps to build effortless code quality and security for developers" - [Codacy](https://github.com/marketplace/codacy)

### id827852934

> automatically update your dependencies
> \- [(View Highlight)](https://read.readwise.io/read/01jfrca9pbr95w8zxrhwv68zv3)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrca9pbr95w8zxrhwv68zv3)
GitHub Marketplace app: "Dependabot Preview"
[Goodbye Dependabot Preview, hello Dependabot!](https://github.blog/news-insights/product-news/goodbye-dependabot-preview-hello-dependabot/)

### id827853571

> automatically optimize all your images
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcqf8m9dm6ftzgvg5et28z)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrcqf8m9dm6ftzgvg5et28z)
GitHub Marketplace app: "Imgbot"
"A GitHub app that optimizes your images" - [Imgbot](https://github.com/marketplace/imgbot)

### id827853644

> the final recipe, which is a GitHub action that runs on a specific schedule.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcsh63b5twr2m5vnqzpgtm)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrcsh63b5twr2m5vnqzpgtm)
Topic #05: Schedule Background Jobs

### id827853693

> This one happens to be a special treat for Firebase users because it solves a common problem: how do I export my Firestore data on a regular
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcv5abc0yv5ks5x360f82d)

### id827853723

> current situation, if the database doesn't provide automatic backups, you need to manually export your data in order to reimagine this recipe.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcw97jfzk2ptsv3hd6m2bz)

### id827853746

> use the on-schedule event and pass it a cron schedule.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcwxnt4qy5z1e9kysmk87s)

### id827853982

> an awesome app called Crontab Guru that can automatically generate schedules for you.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrcyke1ne5kz33dswbsyqa0)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrcyke1ne5kz33dswbsyqa0)
[crontab guru](https://crontab.guru/)
The quick and simple editor for cron schedule expressions by [Cronitor](https://cronitor.io/?utm_source=crontabguru&utm_campaign=cronitor_top&utm_content=38)

### id827885886

> The schedule in this example runs every night at midnight, and then in the action itself, we’re using an action maintained by Google Cloud Platform. This action sets up the G Cloud CLI in the environment, and then we can use it to run a couple of commands to export our Firestore data into a storage bucket.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrfvxymyekgsxd2ej2pkv29)

**Initial thought or note on:** [(View Highlight)](https://read.readwise.io/read/01jfrfvxymyekgsxd2ej2pkv29)
> `.github/workflows/package.yml`
```yml
name: Export Firestore Data
on:
schedule:
- cron: '0 0 * * *'
jobs:
backup:
runs-on: ubuntu-latest
steps:
- uses: GoogleCloudPlatform/github-actions/setup-gcloud@master
with:
service_account_key: ${{ secrets.GCP_SA_KEY }}
export_default_credentials: true
```

### id827889240

> Check the links in the description for a full write-up on how to set up the service account and everything else involved with G Cloud.
> \- [(View Highlight)](https://read.readwise.io/read/01jfrg4p0qddnjdr0w26xc215e)



