---
layout: post
title: Introduction
---

I've finally moved on from my old, homemade blog[^old-blog], and I'm now using [Jekyll](https://jekyllrb.com/).

Why did I do that? The reason is simple:

It took me a lot of time to write a post and it actually made writing less enjoyable, ironically. Let me explain.

# How my old blog worked

I wanted to build my own static site generator from scratch. 

I used **Python** for that. I had a script called `build.py` that would read all the files in the `post/` directory and generate a `index.html` file that would contain all the posts.

Then, I had the idea to introduce templates and components.

**Templates** would be the base of the page, and **components** would be the parts of code that would be reused in multiple pages, such as custom links, horizontal rules, images, etc.

For example, the `link.html` component would look like this:

```html
<!-- link.html -->
<a href="$1$" class="text-dark" target="_blank">$2$</a>
```
And to use it, I would write this in my post:

```html
<!-- post.html -->
Meet <mylink(https://github.com/extremq/float|float)/>.
```

The builder split the text between the paranthesis by the `|` character, and then it would replace the `$1$` and `$2$` with the first and second element of the array[^explanation].

It worked well. It was great. In theory, it was a recursive system that could be used to create any kind of page.

*But in practice*, it was so annoying to write a post. I had to write the HTML code myself, and I had to remember all the components I had.

# The ugly part
`<br>`. 

`<br><br><br>`. 

That was like 50% of my posts.

![br](/assets/images/001/uglycode.webp){:.centered}

Not fun.
{: .caption}

Not only that, but Visual Studio Code would always try and close the HTML tags (`<a></a>`) even though all my components were just a singular closed tag (`<mycomponent/>`).

And it didn't stop there:
- The date was hardcoded as an UNIX timestamp[^unix-timestamp] because I was too lazy to implement a date parser. My god, even something like `2023-05-20` would have been better.
- I had to run the builder every time I wanted to see the changes I made. I also had to refresh the page. I didn't know how to use a daemon[^daemon] to do that for me.
- The styling was based on Bootstrap. It didn't exactly fit my needs, but I didn't want to write my own CSS. That made it hard to customize the site.

So I'm glad I moved on.

# The new blog
This new blog is based on Jekyll. Everyone was praising Jekyll:

> Oh, it's so easy to use! You just write a post in Markdown and it's done!

> You can just use a theme and you're good to go!

> It's so easy to customize!

Ehh... It wasn't *that* easy.

For example, **themes**. I never used Ruby before. It was easy to install `jekyll`, but because of the `Gemfile.lock` file in the themes' repositories, I just couldn't run `bundle install`. I randomly found an issue[^issue] on GitHub that said I should delete the `Gemfile.lock` file and run `bundle install` again and suddenly, every theme worked! I wasted a lot of time on that, sadly.

**Customization** was okay-ish because I knew CSS, but GitHub Copilot[^copilot] had a lot to teach me about. Fortunately, I settled on the thing you see before your eyes and I'm happy with it.

It's fine, though! I'm actually pleased with the result. I recommend Jekyll to anyone who wants to start a blog. By the way, the theme is called [Dark Poole](https://github.com/andrewhwanpark/dark-poole) but with some tweaks added.

# Hosting
I'm hosting this using [Netlify](https://netlify.com). It's free and it's a CI/CD[^ci-cd] service. I just push my code to GitHub and Netlify builds and deploys the site for me. It's great!

> Edit: I'm now using [Vercel](https://vercel.com) because of Next.js which I'm using for my other projects.

I bought this domain from [GoDaddy](https://godaddy.com). Since I am an EU citizen, I could get it really cheap and it has domain privacy[^domain-privacy] included. Less money for GoDaddy, more money for me!

# Conclusion
All in all, this has been a smooth transition. I'm ready to share some of my new projects with you. Stay tuned, cause I've got a lot of stuff on the cooker!

[^old-blog]: It's still available on [extremq.github.io](https://extremq.github.io), and the source code is archived on [GitHub](https://github.com/extremq/extremq.github.io).
[^explanation]: For example, `<mycomponent(a|b|c)/>` would get the arguments `$1$=a`, `$2$=b`, `$3$=c`. You could have as many arguments as you wanted, and they would be replaced in order. I don't think I escaped the `|` character, so you couldn't use it as an argument.
[^unix-timestamp]: The number of seconds since 1 January 1970 00:00:00 UTC. [Wikipedia article](https://en.wikipedia.org/wiki/Unix_time).
[^daemon]: A daemon is a program that runs in the background. It's commonly used to run a program at a specific time, or to run a program when a specific event happens. For example, a daemon could run a program every 5 minutes, or it could run a program when a file is modified. [Wikipedia article](https://en.wikipedia.org/wiki/Daemon_(computing)).
[^issue]: The issue is [here](https://github.com/poole/poole/issues/223).
[^copilot]: Are you a student? If you get Github Pro, you can get access to GitHub Copilot for free! [GitHub Student Developer Pack](https://education.github.com/pack). No, I'm not sponsored by GitHub. I just think it's a great deal. I mean, I wish I was sponsored by GitHub, but I'm not.
[^ci-cd]: Continuous Integration/Continuous Deployment. It's a process that allows you to automatically build and deploy your code. [Wikipedia article](https://en.wikipedia.org/wiki/CI/CD).
[^domain-privacy]: Domain privacy is a service that hides your personal information from the public. When you buy a domain, you have to provide your name, address, phone number, etc. and that information is publicly available. Domain privacy hides that information and replaces it with the information of the company that provides the service. Companies usually make you pay for that privacy and it's annoying. [Wikipedia article](https://en.wikipedia.org/wiki/Domain_privacy).