<h1>
  <span class="headline">EJS Portfolio Lab</span>
  <span class="subhead">Exercise</span>
</h1>

## Introduction

You are going to build a developer portfolio site.

Your portfolio should include:

1. A home page
2. A skills page
3. A projects page
4. A show page for each project
5. CSS styling

Your app will use arrays of objects for the data. You do **not** need a database for this lab.

---

## Learning objective

By the end of this lab, you will be able to use EJS to display dynamic data from an Express server.

---

## App theme

Your app should feel like a beginner developer portfolio.

Imagine you are preparing for a junior developer interview. Your portfolio should help someone quickly understand:

* What skills you are learning
* What projects you have built
* What technologies you used
* What you learned from each project

---

## Minimum requirements

Your app must include:

* An Express server
* EJS view files
* A `public/css/style.css` file
* A skills array
* A projects array
* A page that loops over and displays all skills
* A page that loops over and displays all projects
* A dynamic show page for each project
* Navigation links
* CSS styling

---

## Required routes

Your app should have these routes:

| HTTP Method | Route                  | Page           | Description                   |
| ----------- | ---------------------- | -------------- | ----------------------------- |
| GET         | `/`                    | Home           | Displays a welcome page       |
| GET         | `/skills`              | Skills Index   | Displays all developer skills |
| GET         | `/projects`            | Projects Index | Displays all projects         |
| GET         | `/projects/:projectId` | Project Show   | Displays one project          |

---

## Step 1: Create your EJS files

Inside the `views` folder, create these files and folders:

```bash
touch views/home.ejs
mkdir views/skills
mkdir views/projects
touch views/skills.ejs
touch views/projects.ejs
touch views/projects-show.ejs
```

Your file structure should now look like this:

```plaintext
ejs-portfolio-lab/
├── public/
│   └── css/
│       └── style.css
├── views/
│   ├── home.ejs
│   ├── skills.ejs
│   ├── projects.ejs
│   └── projects-show.ejs
├── package.json
├── package-lock.json
└── server.js
```

---

## Step 2: Create your skills data

In `server.js`, create an array called `skills`.

Each skill must be an object.

Each skill must have at least:

* `id`
* `name`
* `category`
* `level`
* `description`

You should have at least **6 skills**.

Example:

```js
const skills = [
  {
    id: 1,
    name: 'HTML',
    category: 'Frontend',
    level: 'Beginner',
    description: 'I can use semantic HTML to structure a web page.'
  },
  {
    id: 2,
    name: 'CSS',
    category: 'Frontend',
    level: 'Beginner',
    description: 'I can style pages using selectors, colors, spacing, and layout.'
  },
  {
    id: 3,
    name: 'JavaScript',
    category: 'Programming',
    level: 'Beginner',
    description: 'I can use variables, functions, conditionals, loops, arrays, and objects.'
  },
  {
    id: 4,
    name: 'DOM Manipulation',
    category: 'Frontend',
    level: 'Beginner',
    description: 'I can select elements and respond to user events.'
  },
  {
    id: 5,
    name: 'Express',
    category: 'Backend',
    level: 'Learning',
    description: 'I can create server routes and send responses to the browser.'
  },
  {
    id: 6,
    name: 'EJS',
    category: 'Backend',
    level: 'Learning',
    description: 'I can render dynamic HTML pages using server data.'
  }
];
```

You may use this data as a starting point, but you should edit it so it matches your own skills.

---

## Step 3: Create your projects data

In `server.js`, create an array called `projects`.

You must include at least **3 projects**:

1. Your game project
2. Tic Tac Toe / XO Game
3. Rock Paper Scissors

Each project should have enough information to make a useful show page.

Each project should include at least:

* `id`
* `title`
* `description`
* `technologies`
* `features`
* `status`
* `reflection`

Example:

```js
const projects = [
  {
    id: 1,
    image: '/images/screenshot.png',
    title: 'Game Project',
    description: 'A browser-based game built with HTML, CSS, and JavaScript.',
    technologies: ['HTML', 'CSS', 'JavaScript'],
    features: [
      'Interactive buttons',
      'Score tracking',
      'Win or lose message'
    ],
    status: 'Completed',
    reflection: 'This project helped me practice DOM manipulation and event listeners.'
  },
  {
    id: 2,
    title: 'XO Game',
    image: '/images/screenshot.png',
    description: 'A two-player Tic Tac Toe game where users take turns placing X and O.',
    technologies: ['HTML', 'CSS', 'JavaScript'],
    features: [
      'Player turns',
      'Win condition checking',
      'Reset button'
    ],
    status: 'Completed',
    reflection: 'This project helped me understand arrays, indexes, and game logic.'
  },
  {
    id: 3,
    title: 'Rock Paper Scissors',
    image: '/images/screenshot.png',
    description: 'A game where the player competes against the computer.',
    technologies: ['HTML', 'CSS', 'JavaScript'],
    features: [
      'Random computer choice',
      'Player choice buttons',
      'Round result display'
    ],
    status: 'Completed',
    reflection: 'This project helped me practice conditionals and functions.'
  }
];
```

> 💡 You can add more properties if you want, such as `githubLink`, `image`, `favoriteFeature`, or `nextSteps`.

---

## Step 4: Create the home route

Update your `/` route so it renders `home.ejs`.


In `views/home.ejs`, create a simple home page:

Test your route in the browser:

```plaintext
http://localhost:3000
```

## Step 5: Add partial templates

Create a reusable nav partial.  Be sure to link to your CSS file here.


## Step 6: Create the skills index route

In `server.js`, create a route for `/skills`.

Pass the `skills` array into the EJS file.

In `views/skills.ejs`, loop over the skills array.

Test your route:

```plaintext
http://localhost:3000/skills
```

You should see all of your skills displayed on the page.

## Step 7: Create the projects index route

In `server.js`, create a route for `/projects`.

Pass the `projects` array into the EJS file.


In `views/projects.ejs`, loop over the projects array.

Each project should link to its own show page.

Test your route:

```plaintext
http://localhost:3000/projects
```

You should see all of your projects displayed on the page.

## Step 8: Create the project show route

Now create a dynamic route.

This route should use `req.params.projectId` to find one project.


> 💡 `req.params.projectId` comes from the URL.
> For example, if the URL is `/projects/2`, then `req.params.projectId` is `"2"`.

> 💡 `req.params` values are strings.
> That is why we use `Number(req.params.projectId)` before comparing it to the project `id`.


## Step 9: Build the project show page

In `views/projects-show.ejs`, display one project.

This page should show more detail than the projects index page.

It should include:

    - title
    - image
    - description
    - technologies
    - features
    - status
    - reflection


Test each project show page:

```plaintext
http://localhost:3000/projects/1
http://localhost:3000/projects/2
http://localhost:3000/projects/3
```

Each URL should show a different project.



## Step 10: Style your portfolio with CSS

You must use CSS in this lab.

Your CSS should be in:

```plaintext
public/css/style.css
```

Your CSS should include at least:

* Body styling
* Navigation styling
* Card styling for skills
* Card styling for projects
* Spacing with margin or padding
* A hover effect
* A responsive layout using flexbox


You may change the colors, fonts, spacing, and layout.
