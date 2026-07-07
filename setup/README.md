<h1>
  <span class="headline">EJS Portfolio Lab</span>
  <span class="subhead">Setup</span>
</h1>

## Setup

Open your Terminal application and navigate to your `~/code/ga/labs` directory:

```bash
cd ~/code/ga/labs
```

Make a new repository on [GitHub](https://github.com/) named ejs-portfolio-lab.

Clone a copy of your remote repo locally by using the `git clone` command:

```bash
git clone https://github.com/<your-username>/ejs-portfolio-lab.git
```

> 📚 Note: In the link above, where it says `<your-username>`, you should see the username from your GitHub account.

Next, `cd` into your new cloned directory, `ejs-lab`:

```bash
cd ejs-portfolio-lab
```

Now use your class notes to get your express app up and running.  Don't forget to add a `public` folder for your CSS.

Your file structure should look like this:

```plaintext
ejs-portfolio-lab/
├── public/
│   └── css/
│       └── style.css
├── views/
│   └── partials/ 
│       └── nav.ejs
├── package.json
├── package-lock.json
└── server.js
```