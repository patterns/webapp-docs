---
description: Devs guide to getting your code and local set up.
---

# Getting Started

{% hint style="warning" %}
Make sure you have read about our [code base](contributing.md#overview-of-our-codebase), and [how to contribute](contributing.md#first-things-first).
{% endhint %}

## Quick Start

You need Node.js 12 or newer.

To start the project:

1. To create node\_modules run: `npm install`  
2. Create .env.local file and add

```bash
DATABASE_USERNAME = "postgres"
DATABASE_DIALECT = "postgres"
DATABASE_PASSWORD = "postgres"
DATABASE_DATABASE = "bla bla"
DATABASE_HOST = "localhost"
DATABASE_LOGGING = "true"
DATABASE_URL=postgresql://DATABASE_USERNAME:DATABASE_PASSWORD@localhost:5432/DATABASE_DATABASE
```

To start the project run: `blitz start`

## No Blitz?

In case your device didn't recognize blitz, run this command:  
`npm install -g blitz` or `yarn global add blitz`

**Create a New App**

1. `blitz new myAppName`
2. `cd myAppName`
3. `blitz dev`
4. View your baby app at [http://localhost:3000](http://localhost:3000/)

## Need Help?

If you are an active contributor, please discuss in the \#

