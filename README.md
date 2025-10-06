# Dockerized-portfolio-website
**This is my personal portfolio website running in a Docker container with Nginx. Built to showcase Docker skills, containerization, and deployment.**

## Architecture :
* Custom **Dockerfile** creation

* Exposing **port 80** for HTTP access

* Using **Docker volumes** to update the site dynamically

* Understanding **image → container** workflow

![](https://github.com/Shivraj0199/Dockerized-portfolio-website/blob/main/Img/Screenshot%202025-10-06%20121617.png)

---

### Step 1: Create Project Folder Structure 

1. mkdir **portfolio-site**
2. cd **portfolio-site**
---

### Step 2: Add Your Website Files

* **index.html**

```<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Dockerized Portfolio</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Hello, I’m <span class="highlight">Shivraj0199</span> 👋</h1>
        <p>Aspiring DevOps Engineer | Docker & Cloud Enthusiast</p>
    </header>

    <section class="about">
        <h2>About Me</h2>
        <p>This portfolio is running inside a Docker container using Nginx!</p>
    </section>

    <footer>
        <p>📧 Contact: shivrajmohite019@gmail.com</p>
        <p>🌐 GitHub: <a href="https://github.com/Shivraj0199" target="_blank">Shivraj0199</a></p>
    </footer>
</body>
</html>
```
* **Style.css**

```body {
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #0d1117;
    color: #c9d1d9;
    margin: 0;
    padding: 0;
}

header {
    padding: 30px;
    background-color: #161b22;
}

h1 {
    font-size: 2.5em;
}

.highlight {
    color: #58a6ff;
}

.about {
    margin: 30px;
}

footer {
    padding: 20px;
    background-color: #161b22;
}
a { color: #58a6ff; text-decoration: none; }
```
---

### Step 3: Create Dockerfile

```# Use Nginx base image
FROM nginx:alpine

# Copy portfolio files into Nginx web directory
COPY . /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
```

---

### Step 4: Build docker image

```docker build -t portfolio-site .```

---

### Step 5: Run the container

```docker run -d -p 8080:80 --name my-portfolio portfolio-site```

---

### Step 6: Verify running container

``` docker ps ```

![](https://github.com/Shivraj0199/Dockerized-portfolio-website/blob/main/Img/Screenshot%202025-10-06%20115824.png)

---

### Step 7: Check your site 

``` http://127.0.0.1:8080``` or ```http://localhost:8080```

``` http://(ec2-pubic-ip):8080 ```

![](https://github.com/Shivraj0199/Dockerized-portfolio-website/blob/main/Img/Screenshot%202025-10-06%20115309.png)

