<h1>
  <span class="headline">EJS Portfolio Lab</span>
  <span class="subhead">Level Up</span>
</h1>

## Add basic error handling for missing projects

If a user visits a project ID that does not exist, your app should not crash.

Update your show route:

```js

  const selectedProject = projects.find((project) => {
    return project.id === projectId;
  });

  if (!selectedProject) {
    return res.send('Project not found.');
  }

  res.render('projects/show.ejs', {
    project: selectedProject
  });

```

Test this route:

```plaintext
http://localhost:3000/projects/999
```

You should see:

```plaintext
Project not found.
```