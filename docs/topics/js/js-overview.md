[//]: # (title: Kotlin for JavaScript)

Kotlin/JS provides the ability to transpile your Kotlin code, the Kotlin standard library, and any compatible dependencies
to JavaScript. The current implementation of Kotlin/JS targets [ES5](https://www.ecma-international.org/ecma-262/5.1/).

The recommended way to use Kotlin/JS is via the `kotlin.js` and `kotlin.multiplatform` Gradle plugins. They let you easily set up and control Kotlin projects targeting JavaScript in one place. This includes essential functionality
such as controlling the bundling of your application, adding JavaScript dependencies directly from npm, and more. To get
an overview of the available options, check out the [Kotlin/JS project setup](js-project-setup.md) documentation.

## Kotlin/JS IR compiler

The [Kotlin/JS IR compiler](js-ir-compiler.md) comes with a number of improvements over the old default compiler.
For example, it reduces the size of generated executables
via dead code elimination and provides smoother interoperability with the JavaScript ecosystem and its tooling.

> The old compiler has been deprecated since the Kotlin 1.8.0 release.
> 
{type="note"}

By generating TypeScript declaration files (`d.ts`) from Kotlin code, the IR compiler makes it easier to create "hybrid"
applications that mix TypeScript and Kotlin code and to leverage code-sharing functionality using Kotlin Multiplatform.

To learn more about the available features in the Kotlin/JS IR compiler and how to try it for your project, visit the
[Kotlin/JS IR compiler documentation page](js-ir-compiler.md) and the [migration guide](js-ir-migration.md).

## Use cases for Kotlin/JS

There are numerous ways to use Kotlin/JS. Here is a non-exhaustive list of
scenarios in which you can use Kotlin/JS:

* **Write frontend web applications using Kotlin/JS**
    * Kotlin/JS allows you to **leverage powerful browser and web APIs** in a type-safe fashion. Create, modify, and interact
      with the elements in the Document Object Model (DOM), use Kotlin code to control the rendering of `canvas` or WebGL components,
      and enjoy access to many more features that modern browsers support.
    * Write **full, type-safe React applications with Kotlin/JS** using the [`kotlin-wrappers`](https://github.com/JetBrains/kotlin-wrappers)
      provided by JetBrains, which provide convenient abstractions and deep integrations for React and other popular JavaScript frameworks.
      `kotlin-wrappers` also provides support for a select number of adjacent technologies, like
      `react-redux`, `react-router`, and `styled-components`. Interoperability with the JavaScript ecosystem means that
      you can also use third-party React components and component libraries.
    * Use the **[Kotlin/JS frameworks](#kotlin-js-frameworks)**, which take full advantage of Kotlin concepts and its expressive power
      and conciseness.

* **Write server-side and serverless applications using Kotlin/JS**
    * The Node.js target provided by Kotlin/JS enables you to create applications that **run on a server** or are
      **executed on serverless infrastructure**. This gives you all the advantages of executing in a
      JavaScript runtime, such as **faster startup** and a **reduced memory footprint**. With [`kotlinx-nodejs`](https://github.com/Kotlin/kotlinx-nodejs),
      you have typesafe access to the [Node.js API](https://nodejs.org/docs/latest/api/) directly from your Kotlin code.

*  **Use Kotlin's [multiplatform](multiplatform.md) projects to share code with other Kotlin targets**
    * All the functionality of Kotlin/JS can also be accessed when using the Kotlin `multiplatform` Gradle plugin.
    * If your backend is written in Kotlin, you can **share common code** such as data models or validation logic
    with a frontend written in Kotlin/JS, which allows you to **write and maintain full-stack web applications**.
    * You can also **share business logic between your web interface and mobile apps** for Android and iOS, and avoid
    duplicating commonly used functionality, like providing abstractions around REST API endpoints, user authentication,
    or your domain models.

* **Create libraries for use with JavaScript and TypeScript**
    * You don't have to write your whole application in Kotlin/JS – instead, you can **generate libraries from your
      Kotlin code** that can be consumed as modules from any code base written in JavaScript or TypeScript, regardless of the
      other frameworks or technologies you use. This approach of **creating hybrid applications** allows you to leverage the
      competencies that you and your team might already have around web development while helping you **reduce the amount
      of duplicated work**, making it easier to keep your web target consistent with other targets of your application.

Of course, this is not a complete list of all the ways you can use Kotlin/JS to your advantage, but merely some cherry-picked
use cases. We invite you to experiment with different combinations and find out what works best for your project.

Whatever your specific use case, Kotlin/JS projects can use compatible **libraries from the Kotlin ecosystem**,
as well as third-party **libraries from the JavaScript and TypeScript ecosystems**. To use the latter from Kotlin code,
you can either provide your own typesafe wrappers, use community-maintained wrappers, or let [Dukat](js-external-declarations-with-dukat.md)
automatically generate Kotlin declarations for you. Using the Kotlin/JS-exclusive [dynamic type](dynamic-type.md) allows
you to loosen the constraints of Kotlin's type system and skip creating detailed library wrappers, though this comes at the expense of type safety.

Kotlin/JS is also compatible with the most common module systems: UMD, CommonJS, and AMD. The ability to [produce and consume modules](js-modules.md)
means that you can interact with the JavaScript ecosystem in a structured manner.

## Kotlin/JS frameworks

Modern web development benefits significantly from frameworks that simplify building web applications.
Here are a few examples of popular web frameworks for Kotlin/JS written by different authors:

### KVision

_KVision_ is an object-oriented web framework that makes it possible to write applications in Kotlin/JS with ready-to-use components
that can be used as building blocks for your application's user interface. You can use both reactive and imperative programming
models to build your frontend, use connectors for Ktor, Spring Boot, and other frameworks to integrate it with your server-side
applications, and share code using [Kotlin Multiplatform](multiplatform.md).

[Visit KVision site](https://kvision.io) for documentation, tutorials, and examples.

For updates and discussions about the framework, join the [#kvision](https://kotlinlang.slack.com/messages/kvision) and
[#javascript](https://kotlinlang.slack.com/archives/C0B8L3U69) channels in the [Kotlin Slack](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up).

### fritz2

_fritz2_ is a standalone framework for building reactive web user interfaces. It provides its own type-safe DSL for building
and rendering HTML elements, and it makes use of Kotlin's coroutines and flows to express components and their data bindings.
It provides state management, validation, routing, and more out of the box, and integrates with Kotlin Multiplatform projects.

[Visit fritz2 site](https://www.fritz2.dev) for documentation, tutorials, and examples.

For updates and discussions about the framework, join the [#fritz2](https://kotlinlang.slack.com/messages/fritz2) and
[#javascript](https://kotlinlang.slack.com/archives/C0B8L3U69) channels in the [Kotlin Slack](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up).

### Doodle

_Doodle_ is a vector-based UI framework for Kotlin/JS. Doodle applications use the browser's graphics capabilities to draw
user interfaces instead of relying on DOM, CSS, or Javascript. By using this approach, Doodle gives you precise control
over the rendering of arbitrary UI elements, vector shapes, gradients, and custom visualizations.

[Visit Doodle site](https://nacular.github.io/doodle/) for documentation, tutorials, and examples.

For updates and discussions about the framework, join the [#doodle](https://kotlinlang.slack.com/messages/doodle) and
[#javascript](https://kotlinlang.slack.com/archives/C0B8L3U69) channels in the [Kotlin Slack](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up).

### Compose for Web

_Compose for Web_, a part of Compose Multiplatform, brings [Google's Jetpack Compose UI toolkit](https://developer.android.com/jetpack/compose)
to your browser. It allows you to build reactive web user interfaces using the concepts introduced by Jetpack Compose.
It provides a DOM API to describe your website, as well as an experimental set of multiplatform layout primitives.
Compose for Web also gives you the option to share parts of your UI code and logic across Android, desktop, and the web.

You can find more information about Compose Multiplatform on its [landing page](https://www.jetbrains.com/lp/compose-mpp/).

Join the [#compose-web](https://kotlinlang.slack.com/archives/C01F2HV7868) channel on the [Kotlin Slack](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up)
to discuss Compose for Web, or [#compose](https://kotlinlang.slack.com/archives/CJLTWPH7S) for general Compose Multiplatform discussions.

## Kotlin/JS, Today and Tomorrow

In [this video](https://www.youtube.com/watch?v=fZUL8_kgHXg), Kotlin Developer Advocate Sebastian Aigner explains the
main Kotlin/JS benefits, shares some tips and use cases, and talks about the plans and upcoming features for Kotlin/JS.

<video width="560" height="315" href="fZUL8_kgHXg" title="Kotlin/JS, Today and Tomorrow"/>

## Get started with Kotlin/JS

If you're new to Kotlin, a good first step is to familiarize yourself with the [basic syntax](basic-syntax.md) of the language.

To start using Kotlin for JavaScript, please refer to [Set up a Kotlin/JS project](js-project-setup.md). You can also
complete a [tutorial](#tutorials-for-kotlin-js) to work through or check out the list of [Kotlin/JS sample projects](#sample-projects-for-kotlin-js)
for inspiration. They contain useful snippets and patterns and can serve as nice jump-off points for your own projects.

### Tutorials for Kotlin/JS

* [Build a web application with React and Kotlin/JS — tutorial](js-react.md)
guides you through the process of building a simple web application using the React framework, shows how a type-safe Kotlin
DSL for HTML makes it easy to build reactive DOM elements, and illustrates how to use third-party React components and
obtain information from APIs, all while writing the whole application logic in pure Kotlin/JS.

* [Build a full-stack web app with Kotlin Multiplatform](multiplatform-full-stack-app.md)
teaches the concepts behind building an application that targets Kotlin/JVM and Kotlin/JS by building a client-server
application that makes use of shared code, serialization, and other multiplatform paradigms. It also provides a brief
introduction to working with Ktor both as a server- and client-side framework.

### Sample projects for Kotlin/JS

* [Full-stack Spring collaborative to-do list](https://github.com/Kotlin/full-stack-spring-collaborative-todo-list-sample)
shows how to create a to-do list for collaborative work using `kotlin-multiplatform` with JS and JVM targets, Spring
for the backend, Kotlin/JS with React for the frontend, and RSocket.
* [Kotlin/JS and React Redux to-do list](https://github.com/Kotlin/react-redux-js-ir-todo-list-sample) implements
the React Redux to-do list using JS libraries (`react`, `react-dom`, `react-router`, `redux`, and `react-redux`)
from npm and Webpack to bundle, minify, and run the project.
* [Full-stack demo application](https://github.com/Kotlin/full-stack-web-jetbrains-night-sample) guides you through
the process of building an app with a feed containing user-generated posts and comments. All data is stubbed by
the fakeJSON and JSON Placeholder services.

## Join the Kotlin/JS community

You can also join the [#javascript](https://kotlinlang.slack.com/archives/C0B8L3U69) channel in the official [Kotlin Slack](https://surveys.jetbrains.com/s3/kotlin-slack-sign-up)
to chat with the community and the team.