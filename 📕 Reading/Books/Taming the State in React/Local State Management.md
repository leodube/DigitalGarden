# Local State Management

## Definitions
---
### Pure functions
Pure functions is a concept from the functional programming paradigm. It says that a pure function always returns the same output if given the same input. There is no layer in between that could alter the output on the way when the input doesn’t change. The layer in between, that could possibly alter the output, is called side-effect. Thus, pure functions have no side-effects. Two major benefits of these pure functions are predictability and testability.

### Immutability
Immutability is a concept of functional programming, too. It says that a data structure is immutable when it cannot be changed. When there is the need to modify the immutable data structure, for instance an object, you would always return a new object. Rather than altering the object at hand, you would create a new object based on the old object and the modification. The old and new object would have their own instances. Immutable data structures have the benefit of predictability.

### State
**Entity state** is data retrieved from the backend. It could be a list of authors or the user object describing the user that is currently logged in to the application. **View state**, on the other hand, doesn’t need to be stored in the backend. It is used when you open up a modal or switch a box from preview to edit mode.

### Local state
The naming local state is widely accepted in the web development community. Another term might be internal component state.

Local state is bound to components. It lives in the view layer. It is not stored somewhere else. That’s why it is called local state because it is co-located to the component.

In React, the local state is embraced by using `this.state` and `this.setState()`. But it can have a different implementation and usage in other view layer or SPA solutions. The book explains and showcases the local state in React before diving into sophisticated state management with external libraries.

### Sophisticated State
In other resources, you might find it referred to as external state, because it lives outside of the local component or outside of the view layer. Most often, sophisticated state is outsourced to libraries that are library or framework agnostic and thus agnostic to the view layer. But most often they provide a bridge to access and modify state from the view layer. When using only local state in a scaling application, you will allocate too much state along your components in the view layer. However, at some point you want to separate these concerns. That’s when sophisticated state comes into play.

## Unidirectional vs. Bidirectional Data Flow
---
The three advantages in unidirectional data flow over bidirectional data flow are predictability, maintainability and performance

-   **Predictability:** In a scaling application, state management needs to stay predictable. When you alter your state, it should be clear which components care about it. It should also be clear who alters the state in the first place. In an unidirectional data flow one stakeholder alters the state, the state gets stored, and the state flows down from one place, for instance a stateful component, to all child components that are interested in the state.
-   **Maintainability:** When collaborating in a team on a scaling application, one requirement of state management is predictability. Humans are not capable to keep track of a growing bidirectional data flow. It is a limitation by nature. That's why the state management stays more maintainable when it is predictable. Otherwise, when people cannot reason about the state, they introduce inefficient state handling.
-   **Performance:** In a unidirectional data flow, the state flows down the component tree. All components that depend on the state have the chance to re-render. Contrary to a bidirectional data flow, it is not always clear who has to update according to state changes. The state flows in too many directions. The model layer depends on the view layer and the view layer depends on the model layer. That a vice versa dependency that leads to performance issues in the update lifecycle.

## Persistence in State
---
State in applications is often not persistent. When your application start, there is often an initial state. The state updates when the user interacts with the application or data arrives from the backend application. However, you might wonder whether there is a way to persist the state? The question applies to both, local state management and sophisticated management later on.

The obvious answer to this question would be to implement a backend application with a database to persist the state. Extracting the state from your application is called **dehydrating state**. Now, every time your application bootstraps, you would retrieve the state from the backend that keeps it in a database. Once the state arrives in the response asynchronously, you would **rehydrate state** into your application.

### Local Storage

Is there a more lightweight solution compared to a backend application? You could use the native browser API. To be more specific, most of the modern browser have a storage functionality to persist data. It is the lightweight version of a database that is used in the browser. Of course, it is only visible to the user of the browser and cannot be distributed to other users.

Modern browsers have access to the local storage and session storage. Both work the same, but there is one difference in their functionalities. While the local storage keeps the data even when the browser is closed, the session storage expires once the browser closes. Both storages work the same by using key value pairs.

### Caching in State

The local state, later on the sophisticated state as well, can be used as a cache for your application. A cache would make recurring requests to retrieve data from a backend redundant, because they would return the same data as before and the data is already cached in the state.

## The Controversies of Local State Management
---
You can build quite large applications with only local state management. You should be aware of best practices and patterns to scale it, but it is doable. You can spare a lot of application complexity by using plain local state. Once your application scales, you might want to consider using a sophisticated state management library.

Not every state should live in a sophisticated state management. There are use cases when local state is applicable in large applications. Especially when considering entity state and view state: The view state can most often live in a local state, because it is not shared widely across the application. But the entity state can live in a sophisticated state, because it is shared across multiple components. It might need to be accessible and modifiable by multiple components across your application.

## The Flaw of Local State Management
---
What’s the problem with using only local state management? It doesn’t scale in large applications. It doesn’t scale implementation-wise, but it probably doesn’t scale in a team of developers too.

Implementation-wise it doesn’t scale because too many components across your application share state. They need to access the state, need to modify it or need to remove it. In a small application, these components are not far away from each other. You can apply best practices like lifting state up and down to keep the state management maintainable. At some point, components are too far away from each other. The state needs to be lifted the component tree all the way up. Still, child components could be multiple levels below the stateful component. The state would creep through all components in between even though these components don’t need access to it.

Local state can become unmaintainable. It is already difficult for one person to keep the places in mind where local state is used in the component tree. When a team of developers implements one application, it becomes even more difficult to keep track of it. Usually it is not necessary to keep track about the local state. In a perfect world, everyone would lift state up and down to keep it maintainable. In the real world, code doesn’t get refactored as often as it should be. The state creeps through all components even though they don’t consume it.

One could argue that the issues of maintainability apply for sophisticated state as well. That’s true, there are pitfalls again that people need to avoid to keep the state management maintainable. But at least the state management is gathered at one place to maintain it. It doesn’t get too mixed up with the view layer. There are only bridges that connect the view with the state. Thus it is a wise decision to apply sophisticated state management in larger applications in order to tame the state.