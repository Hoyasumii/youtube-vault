Right after I finished building my website (which you can check out in [this article](https://www.tabnews.com.br/hoyasumii/como-eu-criei-o-meu-site-pessoal-depois-de-tantas-tentativas-e-o-que-aprendi-no-processo), I decided to create an API for it. One of the flaws in the older version was the lack of an API capable of updating content automatically.

Unfortunately, I'm currently unemployed and broke, so using services like AWS or Railway was out of the question. That made the API project feel almost impossible, especially since I didn't know where I would host the API or which database to use.

The API's goal was simple: just list my stuff.

I didn’t need a dashboard or a login screen. I just wanted to create routes to display my Articles and Projects. And that got me thinking: **what stack should I choose to publish my applications?**

I've been using **Next.js** in my projects for over a year. Although I have my criticisms of Vercel, I really enjoy working with Next.js, especially because it aims to be a fullstack framework for React. Thanks to its built-in HTTP server, it also supports server-side rendering and route handlers, which allows creating APIs.

This brings me to the first key point:

---

### 1. Choose a Powerful Stack

Picking your own stack is tricky. What will you use for the frontend? The backend? Which database? These questions weigh heavily when publishing a project, even if it's just a portfolio piece.

A good stack can save you hours of headaches and prepare you for issues you'll want to avoid. But if you choose a weak stack, you're bound to hit the worst bugs at the worst times—and that can **COST YOU MONEY**, which we’re clearly trying to avoid here.

Let me walk you through the stack I used to solve one of my biggest problems: creating my API.

It wasn’t that hard to build the API, mostly because I already had some knowledge and relied on the [dev.to API](https://dev.to/guilhermecheng/how-to-use-devto-api-4p65). Dev.to allows you to list the articles you post and filter them by language. Since my site only has two versions (English and Brazilian Portuguese), I created a server-side filter to fetch the right articles and render them dynamically. That made my job much easier. All I had left was to list my personal projects.

**So what backend framework and database should I choose?**

---

The decision came down to **Fastify** vs **Nest.js**.

Fastify is great for backend development and includes native tools for end-to-end testing, which is awesome if you want to implement it.

Nest.js is a REST API framework with strong conventions. That’s good for keeping your code decent, but it suffers from serious internal coupling. Its rigid opinions can complicate long-term development.

To avoid tight coupling in Nest.js, I had to build my own abstractions and factories, which felt like overkill. Honestly, even if deployment wasn't an issue, I wouldn't choose Nest.js—it’s just too bloated for what I needed.

So I postponed choosing a backend framework and turned my focus to the database.

Thankfully, I remembered **MongoDB Atlas**, a managed service offering 500MB of free storage. For small projects, that's more than enough. I used **Mongoose** as an ODM and defined the collection schemas.

Speaking of layers, I followed **Clean Architecture**, even though the project was small. This kept things decoupled and easier to maintain, although it did mean writing a lot more code.

---

### 2. How to Organize Your Project

If you're new to backend development, you'll face many challenges, especially when distributing logic properly across layers. It might take weeks to really understand how it all fits together, but trust me: once you get it, the learning pays off in future projects.

![estrutura-api.png](/estrutura-api.png)

Here's a simple overview of how I organize the heart of my code:

1. Create a **repository layer** for data persistence.
2. Add a **service layer** to handle repository methods, validations, error handling, and data processing.
3. Create a **factory** to return an already-instantiated service.
    

It's a simple flow—but for beginners, it can feel a bit tricky.

![estrutura-api-2.png](/estrutura-api-2.png)

Thanks to this layered structure, I can port the codebase to almost any framework without major rewrites.

---

### 3. Using Next.js to Define Routes

As I mentioned earlier, I’ve been using **Next.js** for a while now. One feature I didn’t like at first—but now swear by—is **Route Handlers**. They’ve become essential for hosting APIs for free.

At first, I didn’t see the point of building APIs inside Next.js. But once I realized how much easier deployment becomes when frontend and backend live together, I started adopting this pattern everywhere.

I thought creating the API would take me 3 days. Originally, I planned to use **AWS Lambda** and **API Gateway** to save costs. But with **Next.js on Vercel**, I got everything working in just a few hours—and still paid **$0**.

---

### 4. Using the Stack in Unusual Contexts

One of the most curious things I’ve done is using **Next.js with EJS**.

For context: when I was learning Node.js a couple of years ago, I built some projects with **EJS**, a template engine for Node. Two of those projects—a blog and a Q&A forum—are still around.

I decided to keep their original external structure but rewrote the backend from scratch, organizing it with a proper architecture.

Rebuilding these old projects was a pain, but also rewarding. There’s something special about bringing an old, broken app back to life—especially when you didn’t even know how to deploy it back then.

Once my portfolio cleanup is done, I plan to build bigger, more exciting projects for myself and for the dev community.

---

### 5. The "Poor Developer"

A poor developer isn't just someone who lacks money or can’t pay for infrastructure. A poor developer is someone who can’t build a project without following exactly what they learned in tutorials.

We’ll all face funny, frustrating challenges in our careers—but we have to overcome them.

When you truly understand your project, you’ll start solving problems in creative ways—and that will motivate you to keep learning.

In one of my rewrites, I replaced **Express** with **Next.js** and kept **EJS** as the template engine. This time, instead of **MongoDB**, I used **Supabase** with **Prisma**—a combination I’d never tried before.

That move solved one of my biggest deployment pains. Now I have two solid, free database solutions I can rely on.

---

I’m really happy with how this project turned out. I built a new version of my site and found unconventional ways to bring my apps to life.

If you're curious, you can check it out here: [https://alanreis.blog](https://alanreis.blog/). Every project on the site links to a public repository. At the time of writing, I'm just finishing two of them—but soon, they’ll all be online.

Thanks a lot to anyone who made it to the end of this article. I appreciate you coming along on this journey!

**Until next time!**