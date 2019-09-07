# Gatsby GitHub Stats

![](https://github.com/lannonbr/gatsby-github-stats/workflows/Update%20Repo/badge.svg)
![](https://github.com/lannonbr/gatsby-github-stats/workflows/Upload%20to%20Firebase/badge.svg)


![Screenshot](./Screenshot.png)

A website that tracks the last two weeks of statistics about the [gatsbyjs/gatsby](https://github.com/gatsbyjs/gatsby) repo.

This is an unnofficial project and not maintained by the Gatsby Core Team.

## Site

The site is a Gatsby site at it's core. It uses a JSON file generated by a GitHub Action as the data source and then passes said data into a variety of charts using the [Recharts](http://recharts.org/) chart library.

To work with the site locally in a development mode:

1. Clone down the repo: `git clone https://github.com/lannonbr/gatsby-github-stats/`
2. Install the dependencies: `yarn install`
3. Run Gatsby in development mode: `yarn develop`

## Actions

There are two actions that continually update the site. They are both found in the `.github/actions/` directory of this repository.

### Github Poller

First off is an action that queries the GitHub [V4 GraphQL API](https://developer.github.com/v4/) for various stats like the number of open / closed issues, PRs, etc. and then sends the stats to a NoSQL database on Google's [Firebase](https://firebase.google.com/) platform.

### Stats Loader

The other action then queries the Firebase database to grab the last 336 entries which equates to the last 2 weeks of data. It then prints it out to a `data.json` file in the `src/data/` directory and then commits it to the repository. This triggers a deploy to Netlify for the site to be rebuilt.
