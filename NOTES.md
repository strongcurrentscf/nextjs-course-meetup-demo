## What are components? Why is React all about them?

React is a JS library for building UI's. It simplifies building UI's by embracing a concept called components. All UI's are made up of componenets.

Components are just a combination of HTML, CSS, and JS. They are resuable with different data.

## React code is written is a 'Declarative Way'!

React uses a declarative approach for building these componenents.
You will not give React imperative instructions... instead you will always define the desired end-state and under what conditions, and it's then Reacts job to figure out how and what it needs.

## Creating a React project.

The easiest way to get started is to use a tool called 'Create React App'.

- create-React-app.dev for full documentation.

There you will find what you need to create a React project.

- pre-configured folders with some basic React code files and a bunch configuration files which help build React app for productions use. There will be a couple of transformation and optimization steps between developing and running a React app in production.

- node.JS needs to be installed to run command to create React project and environment.

- navigate to folder to contain the React project and run "npx create-react-app :NameProjectHere:"

This will create new React project in the destination and create a folder with the name you picked and inside of that folder it will set up all of the key files to write and build React application. Happy Hacking!

- cd into the named project folder and run "npm start". localhost:3000

This will create a src folder and a package.json file.

## Analyzing a standard React project.

The index.js file found in the src folder will be the first file executed when the page is loaded... well, not exactly that code but a transformed version of that code behind the scenes. 'react' and 'react-dom' packages in the dependencies do these transformations.

- React-DOM object is imported into index.js to then call a method, render(), that is on that imported object.

- React-DOM.render() takes 2 arguments/parameters...

  - the second paramater is a JavaScript DOM API method which we're calling on the global document object to select a certain element by it's ID.
  - This ID points to an element in the 'public' folder... we rarely work in this folder but it holds the single HTML file which is loaded by the browser... because with React, we build a so-called single page application. It means that only 1 HTML file is deliverd to the browser, hosted by the browser, rendered by the browser.
  - On this single HTML file we import the finished React app code and it is that code that updates what we see on the screen. We import that code into the single div there with an ID of "root". So basically the contents of that div should be replaced by the contents of React-DOM.render()'s first argument, "<App />".

- <App /> is also being imported from one of our JS files. It is a component. It is this App component that we render in place of the contents of the div with ID "root". "< />" this is JSX syntax.

App.js file is a that holds a function named App that we export default.

- This functions returns HTML code. Not valid JS but is JSX... a special syntax invented by the React team.

## Introducing JSX.

JSX code is basically HTML inside of JS. Indeed JSX stands for JavaScript XML because HTML is, in the end, XML.
It is developer friendly code that is transformed behind the scenes.

## How React Works

We have HTMLish code in the App function, and we have that code there because with React we build our own custom HTML elements... we build those components. A component is basically a custom HTML element.

- We do that with a Declarative approach. Which means that with React, we define the desired target state and React is then responsible for generating and running the actual DOM instructions which update what's on the screen.

## Building a First Custom Component

A component in React is just a JS function.

Organize component JS files into appropriate folders. Adhere to NamingConvention.

- export default the function so that we can import it like a regular HTML element inside of the HTML code written in the App() component. Hence at the top of the App.js file we should import "ExpenseItem" from "./components/ExpenseItem".
- We can use this like an HTML element by using the opening and closing tags. key difference is that they arent starting with a lowercase but an UpperCase. Your own custom components must begin with an uppercase so that React is able to detect that this is a custom component. Lowercase elements are recognized as built-in elements.

## Writing More Complex JSX code

In React there is an important rule regarding the JSX code you return inside of a component... You must only have 1 root element per return statement/JSX code snippet.

- One of the easiest work arounds is to wrap the multiple elements into a parent div. Opening and closing div tags. We can improve the readability by wrapping in parenthesis to signal to JS that this is one statement, even if multiple lines.
- Inside of that main div we can have multiple elements side by side.

## Adding Basic Styling

We use CSS. We typically add the .css file, of the same name, next to the component file.

- To make the build process aware of this .css file we import it in our component file. "./ExpenseItem.css".
- This tells the build process that the .css file should be considered.

Inside of that CSS file we prepare .css classes that can be added to elements to apply a certain look... In our HTML code in ExpenseItem.

- We don't type "class=" to our element's opening tag like in regular HTML, but instead, "className=". JSX syntax.

## Outputting Dynamic Data & Working with Expressions in JSX

Why Components?
Split big chunks of code into multiple smaller functions.

- Reusability: Don't repeat yourself.
- Separation of Concerns: Don't do too many things in one and the same place (function)

We can use JS to create const variables and output the values in the component's JSX return snippet using single curly braces. In these curly braces we can run basic JS expressions or just point to a variable or constant. JS will extract the value stored in this const and inject is into the JSX/HTML return snippet.

Now it is not hard coded into the JSX code but output dynamically and the concrete value is taken from that constant. Dynamic placeholders!

## Passing Data via "props"

We can make our components reusable by using parameters and a concept called "props" in React.

We can pass data to a custom component by adding an attribute, and inside of that component we can then get access to all the attritutes which might have been set on our custom component.

In App.js we can add attributes(props) to these custom HTML elements and access the key/value pairs in the ExpenseItem function by passing the single "props" object as parameter. From here we can access the attributes through the props namespace.

## Adding "normal" JavaScript Logic to Components.

We are basically done with our first custom component. The ExpenseItem component is now reusable. We can use the props concept to configure it differently every time that we're using it. So that the 4 times that we're using it in App.js
as <ExpenseItem></ExpenseItem> we get a different output 4 times.

The method .toLocaleString() method is available on all date objects. It helps with outputting dates in human readable formats. First parameter is language, second is an object where we configure specific format. See MDN for options.

## Splitting Components Into Multiple Components

Components eventually become bigger and bigger. React allows us to split components into smaller building blocks where each one is focused on one core task and can be combined to build the overall UI. Components stay small and manageable.

The "calender" item in the JSX expense-item could be treated as a separate component. Our second custom component. ExpenseDate.js to render the date of an expense.

We now have multiple components and they are nested inside of each other... In the App component we are using the ExpenseItem (Expenses) component and inside of the ExpenseItem component, we're using the ExpenseDate component. We're also forwarding our data with the help of props through these multiple components.

## The Concept of "Composition" ("children props")

Compoents really just are these custom HTML elements where we combine HTML code(JSX) and styling and axtra JS logic.

This approch of building from smaller blocks is called Composition.

What if we wanted to create a component just just serves as a shell around any other kind of component.

At the moment we have highly specific components.

- ExpenseDate is about outputting a date. Formatted and styled.
- ExpenseItem is about outputting an expense item.

All of these components are also only configured through props.

Sometimes we want to have a component where we dont configure everything through props but instead be able to pass content between the opening and closing tags of that component.

The idea of having these componets is to have reusable blocks and to avoid code duplication. Here at the moment we at least have some style duplication also some HTML structure duplication.

- Expenses has a container div
- ExpenseItem has a container div

We could extract these surrounding container divs and extract the styles they have in common like rounded corners and a drop shadow, into a seperate component.

We could name such a component, "Card".
Such a Card componet is still a regular component. It could return a div or any other kind of HTML container element with a className of card. And then we can add a Card.css file and import these styles into the Card component.

We could cut the border-radius and the box-shadow from Expenses.css and paste them into Card.css inside of a .card css selector.

We will remove the same styles from ExpenseItem.css and will use the card component in it's place.

This Card component will not be configured through some attributes. Instead the idea would be to replace the built-in divs with our custom Card container component which have their predefined styles automatically.

Out of the box we can't use our custom components as wrappers around other kinds of content. Having content between opening and closing tags doesn't work like the built-in HTML elements like div and h2.

To make our custom Card wrapper component work, in Card.js we want to accept props but we will not be working with attributes. Instead a speacial prop which is built into React, which every component receives even if you're not setting it explicitly.

This is a prop who's value we want to output between the opening and closing tags of the JSX div return inside of the Card component function.

It's the "props.children" prop.

Children is a reserved name. We don't set a children prop when using Card. The value of this special children prop will always be the content between the opening and closing tags when using our custom component.

Card being a custom component made by us, it's style is still a bit broken here. The reason for that is that we extracted some styles which ExpenseItem A and Expenses had in common, but we had more styles for these which are also important to include. Just setting the className to a css selector will not work on a custom container like Card. Custom components will only support what you tell them to support.

If we want to be sure that a className can be set on our custom component and has an effect, we have to tweak the code in the Card component. We want ot tweak it such that we add whatever is set as a className on Card when we use it to the className string we're setting as className on the Card div.

We can access that classList through the className prop set when using the Card component in ExpenseItem.js.

So now anything we receive as a className from the outside is added to the className string in our Card JSX return.

## A Closer Look At JSX

We used to have to import React from "react" in every file where we use JSX syntax code. Today we can omit this import.

If we didn't use this JSX syntax we would use this alternative:

- React.createElement(
  'div',
  {},
  React.createElement("h2", {}, "Let's get started!"),
  React.createElement(Expenses, { items: expenses })
  ):

createElement takes 3 parameters:

- the first argument is the element which should be created. ie. a "div"
- second is an object which configures these element. An object which sets all the attributes of this element... this div has no attributes sohere we can pass in an empty object.
- the third argument is the content between the opening and closing div tags. Not just the third argument but any one after that will be considered content between the opening and closing div tags.

We imported and added React to our files because in the past it was always necessary to all components which used JSX code.

Also, this is why we always need a wrapper when trying to return elements that are side by side.

## Organizing Component Files

Group by utilities... components .. Expenses, NewExpense, UI

## An Alternative Function Syntax

Write arrow functions using const.

## Module Introduction ## SECTION 4

Closer look at User Interaction and handling user events like clicks or input into text fields and so on.

And we're going to have a look at the very important concept of State in React apps.

Knowing that React uses a Declarative approach where we define desired target states and React takes care of reaching that state,we will build more than static apps where the state never changes.

We want apps that are interactive.

- Handling Events
- Updating the UI and working with "State"
- A closer look at components and state.

## Listening to Events and Working with Event Handlers

Added a <button></button> to the ExpenseItem JSX labeled "Change Title".

When that button is clicked we want to change the title.

All built-in HTML elements, we have full access to native DOM events which we can listen to. For all of these default events there is a prop equivalent in React which you can ad to these built in HTML elements to listen to these events.

These props all start with "on". React exposes all these default events as props that start with "on".

When define what should happen on the event. The value code that should eventually be executed. We define values that should eventually be executed as a function. All these onEvent handlers want a function.

We want to keep our JSX code lean and clean so we typically would store this function in a const variable outside of the JSX block and point to it. It is convention to name event handler functions after event and ending in Handler.

## How Component Functions Are Executed

We never call our component functions explicitly. Instead we just use these functions like HTML elements in the JSX code.

Under the hood, the JSX is almost liek a function call. By using our components in JSx code, we make React aware of our component functions. React calls these component functions whenever it evaluates our JSX code. Then calls any further component functions that those functions might have returned, until ther ae no more functions left.

Then it evaluates the overall result and translates that into DOM instructions to render on the screen.

It's all started by the index.js file where we initially point at the <App /> component with ReactDOM.render()... and that happens when the React app is being loaded on the screen... which happens when the page is being visited and first loaded... AND DOESNT REPEAT THAT INITIAL LOAD/CALL.

To have Raect reevaluate a certain component to update the UI, React introduces a special concept called State.

## Working with "State"

The handler, which changes the value of "title", shoud result in this ExpenseItem component instance being re-evaluated.

By default, regular JS variables do not trigger such a re-evaluation. React doesnt care about that.

To tell React that it should call the function again and re-evaluate, we need to import something from the React library. We do this by adding a "named import":

- import React, { useState } from "react"

useState is a function provided by the React library and this function allows us to difine values as "state" where any changes to these values should reflect in the component function being called again.

Using the useState function:

- inside of our component function, we called useState().
  It is a "React Hook". One of many hooks in React and can be recognized by by the fact that they start with the word "use". All these hooks must only be called inside of component functions. They cant be called outside of a component and shouldnt be called in any nested functions.

- useState() wants a default state-value.
  With useState we create a special kind of variable. A variable where changes will lead to this component being called again. So we assign an initial variable: useState(props.title)

  Now this special variable is created. useState returns access to the variable to use in our JSX.

  It also returns a function which we can call to assign a new value.

  useState always returns these 2 values in an array. Where the first value is the variable itself. And the second value in the array is the updator function.

- We typically use array destructuring to store both elements into separate variables or constants:
  const [title, setTitle] = useState(props.title)

- We assign a new value by calling setTitle() and passing the new value as an argument:
  setTitle("Updated ✨")

Calling this function does not just assign a new value to some variable. It is a special variable to begin with that is managed by React somewhere in memory... and when we call this the special variable will not just receive a new value BUT the component function in which you called this state updating function and in which you intialized your state with useState() will be excuted again and render any changes onto the UI.

## A Closer Look at the "useState" Hook

Why use const to declare the useState variables to store the State and the State-Updating function?

- useState registers some value as a State for the component in which it is being called... More specifically, it registers this for a specific component instance.
  For example, in Expenses.js we have 4 ExpenseItem instances. Every instance receives it's own seprate State which is detached from the other States.
- Whenever State changes, it's only the specific instance that React will re-evaluate.

- We're not assigning a value to title with the (=) sign. By calling useState we tell React that it should manage some value for us... We never see that variable itself. We just call the function to create and manage it.

- React keeps track of when we call useState in a given component instance for the first time so that setting/calling useState on "props.title" doesnt get overwritten every time the component is re-evaluated. The State in useState is only initialized once and afte recognizing this, React will just return the lastest State.

## State can be updated in many ways!

You can update states for whatever reason you may have.

## Adding Form Inputs

We want to add the capability to gather user input.

- Add sub-folder "NewExpense" in the components folder to separate the components that that send data to the UI from the ones that receive it.
- Create newExpense.js in NewExpense folder for NewExpense const component function.

The goal of this component function is to return a form for our inputs. With styling(div) around that <form></form>.
... We actually took the form and put it into a separate component so that the form logic lives in it's own component.

We added the components but we need to gather the inputs. onKeystroke or onChange. And when the form is submitted, we need to take the inputs and combine them into a new expense object.

## Listening to User Input

We need to add listeners to listen for every keystroke or every change of these inputs. We can do that on the element taht we want to add a listener to by adding a prop that starts with "on" and the name of the event. We'll use onChange because we can use it in all input types.

On the onChange prop we pass a pointer to the titleChangeHandler() function, as a value.

Every event listener returns an event object. We can use this object to target the target field, which in this case is <input>, and this input element has a long list of properties, which we can read and set.

It also has a value property. This value property holds the current value of this input field at the point in time the event occured.

## Working with Multiple States

We want to make sure that we store the input value somewhere so that when the form is submitted we can use that value to combine it into an object.

To make sure that we store the value and that it survives if that function would be re-executed, we can again use State.

- import the useState hook from React and call it at the beginning of the ExpenseForm component function and set the state for the input.

You can call useState more than once. All of these states inside of the same component will be seperate from each other.

## Using One State Instead (And What's Better)

We can monitor all <form> <input> states by calling useState({}) once and passing in an object. In this object we can group together all of our initializing states.
The difference is that whenever we updsate this State, we need to update all and not just one.

Merging states into one:
const [userInput, setUserInput] = useState({
enteredTitle: "",
enteredAmount: "",
enteredDate: "",
});

We have to ensure that the other pieces of data don't get lost. If we were to set the new user input state to an object with just one key/value pair, we would lose the other keys because when we update our State, React wil NOT merge this with the old state. It will replace the old state with the new state. To preserve the other keys we need to manually copy them even though they are not updating.

One way of doing this would be to use the spread operator (...) and override the key to be updated.

setUserInput({
...userInput,
enteredTitle: event.target.value,
});

## Updating State Thst Depends On The Previous State

Whenever we update state and you depend on the previous state we shouldnt really use the above spread operator method.

Instead, we should pass in a function to that state updating function. This inner arrow function will receive the previous State that is default available to useState's updating function. We can then return the spread (...) of this prevState and override any keys.

Keep in mind that React schedules these state updates. With this prevState method we can ensure we receive the latest state snapshot.

If our state update depends on the previous state, we should we should use this prevState function form.

## Handling Form Submission

Submit the form when the button is pressed by gathering the different state slices and combining them into one object.

We want to listen to the form being submitted. We could add an onClick to the button but this would not be the bast way of listening here. There is a default behavior built in to the browser... if a button especially with the sumbit type is pressed inside of a form, this overall form element will emit an event for which we can listen for. The "submit" event.

So it's ont he form where we want to listen for onSubmit.

- save the onSubmit callback function in a seperate variable and point to it in the JSX.
- Combine all user input data into 1 object from the value stored in the "enteredVariable" useState array.

## Adding Two-Way Binding

How can we clear the form inputs?

By using useState we can implement something called two-way binding. Which means that for inputs we dont just listen to changes but we can pass new values into the input so that we can reset or cahnge the input programatically.

We have to add the value attribute to the input element. This will set the value to what we want it to.

Here we will bind it to {enteredTitle}. This is two-way binding because we dont just listen to changes in the iput to update our state, but we also feed the state abck into the input... so that when we change the state, we also change the input.

When the form is submitted we can call setEnteredTitle('') and set the input value back to an empty string.

## Child-to-Parent Component Communication (Bottom Up)

How do we pass data from child to parent?

We technically dont need the "expenseData" in the ExpenseForm component. It'd be a better fit to have this in the NewExpense or better in the App.js because there, we have our "expenses" array.

Ultimately our goal will be to add a new expense object to the expenses array and enrich it by adding an id.

So we need to pass the data which we're collecting and generating in ExpenseForm to the App component. Up to this point we only learned to pass data from parent to child.

In ExpenseForm we're listening for user input (onChange).

- When triggered by change, onChange executes the "titleChangeHandler" function.
- At "titleChangeHandler" we get the default event object.

We can think of the input element as a component as well provided to us by React/JS/Browser. We set props on this input component, including the onChange prop, that wants a function as a value, and then internally, the input JSX element adds the event listener on the rendered input HTML element.

We can replicate this pattern for our own components as well.

- We can create our own event props that expect functions as values.
- The function as value would allow us to pass a function form a parent component to a child component. And call that function inside of the child component.
- When we call a function we can pass data to that function as a parameter... communicating UP from child to parent.

With our own component??

Let's say we want to pass the expenseData that we gather in the ExpenseForm component to the NewExpense component as a 1st step. We ultimatley want to reach the App component. We cant skip a parent or child when passing props.

To make sure we pass the data from ExpenseForm to NewExpense, we need to add a new prop to <ExpenseForm/> where it's being used in NewExpense.

It's our component so we can name it whatever we want.
We'll name it "onSaveExpenseData". It's convention to name it 'on' to make it clear that the value for this prop should be a function which can then be called inside of the <ExpenseForm/>.

Just as we did for the input element's onChange prop.
So, in the NewExpense function body we should define the function: "saveExpenseDataHandler"

- which will expect the user entered expense data: "(enteredExpenseData)"

- in this function body we can copy in the (...enteredExpenseData) object with spread op. We expect this object to be the one generated in ExpenseForm's 'submitHandler'. Then add a new key to the object, ("id"), and simply set it to Math.random...

Now this is the function we want to pass/point to in our NewExpense JSX, so that <ExpenseForm/> can use it to make our id'd data object.

The 2nd step is to use this function inside of our ExpenseForm component body. We didnt have to do this for the built in <input/> version of child/parent bottom-up communication. But we still passed a function to onChange in the input props and internally React add the listener and knows to call the function when the event occurs.

Doing it on our own function, we have to call the passed in function manually:

- So in ExpenseForm.js we can now expect the "onSaveExpenseData" prop we set on it in the JSX where we use it.
- Access the props by adding "props" to the ExpenseForm function parameters.
- Use the prop function inside of the event handler function (submitHandler) by accessing and executing props.onSaveExpenseData() and passing, to this prop function, the "expenseData" available in this submitHandler function.

We can execute it here because the value of the prop we passed/accessed is a function. This is a super important pattern which we will use alot in React.

To further pass the object from NewExpense to App,

- we create a handler for this expense data: "addExpenseHandler"... will receive object
- pass this function into props of <NewExpense/> in App's JSX.
- in NewExpense.js add "props" to component's function parameters and call the function in NewExpense's saveExpenseDataHandler, passing the expenseData available.

## Lifting The State Up

States can be shared between siblings only through a shared parent.

## Assignment 2: Working with Events and State

- Access the state of the filter by adding onChange event listener onto the <select> element and an eventHandler to store const = event.target.value.
- In Expenses.js, the parent where we use/render <ExpensesFilter/>, add an "event" prop that points to a function... that function will receive the <select> value data.
- It receives the data by being called in the child component, ExpensesFilter.js eventHandler, with the data collected through onChange event's target value.
- Import and set useState("2021") to const [filteredYear, setFilteredYear] to store with React.

## Contrailled Vs. Uncontrolled Components and Stateless Vs. Stateful Components

<ExpensesFilter/> is a so called Controlled Component.
see Smart and Dumb components.

## SECTION 5: Rendering Lists and Conditional Content

## Module Introduction

Made rendering expenses from App.js in Expenses.js dynamic by using map method on expenses array to render ExpenseItem for each.

## Using Stateful Lists

Rememeber to use the function version to update useState when the next state is depending on the previous one...

const addExpenseHandler = (expense) => {
setExpenses((prevExpenses) => {
return [expense, ...prevExpenses];
});
};

## Understanding "Keys"

React has a special concept when it comes to rendering lists of data. It exist to ensure that React can update and render such lists efficiently.

Without keys, React will add an item to the end of the list then visit each item to render it as specified by our array order... re writing any states we might have assigned to an ordered item in our array.

We have a way of identifying and telling React where a new item should be added.

- We go to the place in JSX where we output our list of items and add a special prop to the item, "key".
  <ExpenseItem
  key={expense.id}

- If we dont have unique ids, we can add "index" as a parameter to the mapping function. But we can still run into bugs because the index for a given item is not directly atteched to the content of the item.

## Assignment 3: Working with Lists

{props.items
.filter(
(expense) =>
filteredYear ===
expense.date.toLocaleString("en-US", { year: "numeric" })
)
.map((expense) => (
<ExpenseItem
              key={expense.id}
              title={expense.title}
              amount={expense.amount}
              date={expense.date}
            />
))}

## Outputting Conditional Content

Conditional content is about rendering different content under different conditions.
Ternary:

- {filteredExpenses.length === 0 && <p>No expenses found.</p>}
  {filteredExpenses.length === 0 ? (
  <p>No expenses found.</p>
  ) : (
  filteredExpenses.map((expense) => (
  <ExpenseItem
              key={expense.id}
              title={expense.title}
              amount={expense.amount}
              date={expense.date}
            />
  ))
  )}

Short-Circuiting:

- {filteredExpenses.length === 0 && <p>No expenses found.</p>}
  {filteredExpenses.length < 0 &&
  filteredExpenses.map((expense) => (
  <ExpenseItem
              key={expense.id}
              title={expense.title}
              amount={expense.amount}
              date={expense.date}
            />
  ))}

Conditional Variable:

- let expensesContent = <p>No expenses found.</p>;
  -------> NOTE the JSX outside of return block. Still works!

  if (filteredExpenses.length > 0) {
  expensesContent = filteredExpenses.map((expense) => (
  <ExpenseItem
          key={expense.id}
          title={expense.title}
          amount={expense.amount}
          date={expense.date}
        />
  ));
  }

  return (
  <div>
  <Card className="expenses">
  <ExpensesFilter
            selected={filteredYear}
            onChangeFilter={filterChangeHandler}
          />
  {expensesContent} <------- conditional variable
  </Card>
  </div>

## Adding Conditional Return Statements

We extracted the expenses list logic into a new component: ExpensesList.js

const ExpensesList = (props) => {
if (props.items.length === 0) {
return <h2 className="expenses-list__fallback"> Found no expenses.</h2>;
}

return (

<ul className="expenses-list">
{props.items.map((expense) => (
<ExpenseItem
          key={expense.id}
          title={expense.title}
          amount={expense.amount}
          date={expense.date}
        />
))}
</ul>
);
};

Here we're handling if/when there are no expenses to render, in which case, we return an <h2> "Found no expenses".

Else, we return our <ul> with <ExpenseItem/>.

## Assignment 4: Conditional Content

Making ExpenseForm conditional, so that when we submit or cancel on form, it renders Add New Expense button, which when clicked, renders the form.

This means we have to register a new State here...
We have the state when the form is open for editing... and the state when we are not editing an expense and the button should be showing.

We simply need a true/false state which says whether the form should be showing or not.

const NewExpense = (props) => {
const [isEditing, setIsEditing] = useState(false); <=== BOOLEAN STATE

const saveExpenseDataHandler = (enteredExpenseData) => {
const expenseData = {
...enteredExpenseData,
id: Math.random().toString(),
};

    props.onAddExpense(expenseData);
    setIsEditing(false);

};

const startEditingHandler = () => {
setIsEditing(true);
}; <=== SETS isEditing TO TRUE. Triggered when the Add New Expense <button> is clicked.

const stopEditingHandler = () => {
setIsEditing(false);
}; <=== SETS isEditing TO FALSE WHEN CANCEL IS CLICKED IN ExpenseForm.js BY PASSING A POINTER TO THIS HANDLER THROUGH OUR USE OF ExpenseForm IN NewExpense JSX.

BUTTON IN ExpenseForm.js:
{{{(((
  <button type="button" onClick={props.onCancel}>Cancel
  </button>
)))}}}

return (

<div className="new-expense">
USE isEditing TO DETERMINE WHICH ELEMENT TO SHOW. SEE THE 2 DYNAMIC EXPRESSIONS IN {}. SHORT-CIRCUITING
{!isEditing && (
<button onClick={startEditingHandler}>Add New Expense</button>
)}
{isEditing && (
<ExpenseForm
          onSaveExpenseData={saveExpenseDataHandler}
          onCancel={stopEditingHandler}
        />
)}
</div>
);
};

## Demo App: Adding a Chart

Chart and ChartBar components.

Chart:

- chart component expects props and will be rendering ChartBars. import ChartBar and it's CSS.
- return a <div className="chart"> to contain our ChartBars.

We could say that when the ChartBar is being used somewhere, in our application, we want to receive the dataPoints that should be plotted, as props.
So that the Chart component is fairly configurable and the components that use the Chart can decide how many dataPoints, with which values, should be rendered.

- we output the ChartBars dynamically by going through an Array of dataPoints an mapping every dataPoint to the ChartBar.

- on props namespace we could expect our dataPoints and we expect that to hold a value which is an Array... to call map on and map every dataPoint into a ChartBar component. We create as many bar components as we have dataPoints.

- we want to pass data into the <ChartBar/> to control how it will be rendered. For this we want to extract some data from the incoming dataPoints. The ChartBar element should receive a "value" prop equal to dataPoint.value...
- We'll read into this prop in the ChartBar.js and that when we define dataPoints later, that every dataPoint has a "value" property... We'll need a dataPoint that is an object which has a value property.
- We also want to make sure that every ChartBar plots the value in relation to the maximum value in the entire chart... Therefore we also want to pass in a maxValue property and set it to "null" for now.
- We wan to have a label for the months so we add a label prop and set it to dataPoint.label.

- And since we're mapping the dataPoints, we also want to add a key prop to help React render these list items efficiently. Set a key prop to dataPoint.label too since every month will have a unique label.

## Adding Dynamic Styles

ChartBar:

- ChartBar component expects props that we defined in Chart.js.

- <div className="chart-bar"> with a nested <div className="chart-bar__inner"> with a further nested <div className="chart-bar__fill">

- Next to the first inner div, <div className="chart-bar__label">. This div will display the {props.label}

"chart-bar\_\_fill" is missing the height in it's css. This height, or how much we fill that bar will depend on the data we're receiving. The value prop in relation with the maxValue.

To calculate by how much a specific ChartBar instance should be filled:

- We add a let variable, barFillHeight and set it to "0%".

- check for if (props.maxValue > 0) and if thats the case, we want to set barFillHeight to {
  barFillHeight = Math.round((props.value / props.maxValue) \* 100) + "%"
  }

"+ '%'" converts the number to the string we need to add height to "chart-bar\_\_fill" styles

- to add a style to an element dynamically:
- add the style prop set to a {dynamic value}
- style wants an object as the dynamic value. Looks like double curly braces {{}}
- use the css property key names with their values. Set "height: barFillHeight"

## Wrap Up and Next Steps

Added new component, ExpensesChart.js.

ExpensesChart expects props with the goal of return the <Chart/>.

- import Chart
- define the dataPoints which are to be passed into the Chart return body where we are referring to these dataPoints prop.

To define these dataPoints we create a new const in ExpensesChart named ChartDataPoints = [{}]. An array with a bunch of objects... because we expect every dataPoint to be an object in Chart.js when we map through the dataPoints.

- each object should have a label: "Jan" and a value: 0... add this object for all 12 months.

We dont want to have zero for every dataPoint. We want to have a look at our filteredExpenses and make sure that we go through all the expenses for a selected year and that we sum up the expenses for the different months, and assign them in chartDataPoints.

So we expect to get the filteredExpenses as a prop on the ExpensesChart component because we will use ExpensesChart in the Expenses.js file later.

- add for-loop to get month(0-index format) and update the value of the appropriate dataPoint by the expense amount by adding something to it wiht the (+=) shortcut operator:

for (const expense of props.expenses) {
const expenseMonth = expense.date.getMonth();
chartDataPoints[expenseMonth].value += expense.amount;
}

- Now we can pass these dataPoints to the <Chart/> element by passing the updated chartDataPoints in ExpenseChart's JSX:
  return <Chart dataPoints={chartDataPoints} />;

We still need to calculate the total maxValue... We want to look at all the months and find the biggest value across all months:

- We add a new constant in Chart, totalMaximum and set it to Math.max(), which expects comma separated arguments for which it then returns the biggest number... We map the values to another constant, dataPointValues, using map and spread out the array for Math.max:

const dataPointValues = props.dataPoints.map((dataPoint) => dataPoint.value);

const totalMaximum = Math.max(...dataPointValues);

Now we just have to use our ExpensesChart component in the Expenses.js file between the <ExpensesFilter/> and <ExpensesList/>,
passing in our expenses prop:

<ExpensesChart expenses={filteredExpenses} />

## SECTION 6: Styling React Components

## Module Introduction

There are different techniques for setting styles dynamically or styling components such that other components are not affected by this single component's style.

Right now the CSS styles we are using are global styles.

Scoping styles to components.

## Setting Dynamic Inline Styles

Inline styles get priority over the stylesheet styles.

## Setting CSS Classes Dynamically

Use Template Literals to add/remove style classes dynamically.

## Introducing Styled Components

To have our CSS style classes not be be scoped globally:

- Using Styled-Components package:

  - npm install --save styled-components
  - Use a Tagged Template Literal:

    - import styled from "styled-components";
    - const Button = styled.button``;

      Tagged Template Literals are a default JS feature. Button is simply a method on this styled object. What we pass between the 2 back ticks will end up in the button method which will return a new button component... with the styles we provide between the 2 back ticks.

    - copy the button styles into the back ticks.

    Get rid of any .selectors. And for pseudo-selectors, use the & symbol.

    .button:focus {
    outline: none;
    }

    &:focus {
    outline: none;
    }

    - we should now have a button with all the back tick styles applied.
    - any props we might be passing to our button are applied by default.

    We can get rid of the React import now because we are not dealing with JSX.

## Styled Components and Dynamic Props

Using Styled-Components for our

<div className={`form-control ${!isValid ? "invalid" : ""}`}>
  <label>Course Goal</label>
  <input type="text" onCha  {goalInputChangeHandler} />
</div>

If we're only using this <div> form component in this file, we can create a new styled-component in the same file:

- create new const component (FormControl)
  const FormControl = styled.div``

- replace
  return (

      <div className={`form-control ${!isValid ? "invalid" : ""}`}>

  );

  with
  <FormControl className={!isValid && "invalid"}>

  We can do this imperative class naming BUT we can also utilize another feature provided by styled-components:

We can also add props to our styled component:

- <FormControl invalid={!isValid}>
- this "invalid" prop can be used between the back ticks of the styled-component
- we go to the place where we want to control the input border color, and since we between back ticks, we can use the ${} syntax.
- here we pass in an arrow function which receives props as a parameter and returns the text that should be the CSS value for the particular key/value pair.

border: 1px solid ${(props) => (props.invalid ? "red" : "#ccc")};

Style-Component will call this arrow function and for props it will feed all the props we passed in to the component in JSX... the "invalid" prop.

## Style Components and Media Queries

Adding a media query to the button:

- Added default width for the button to 100% in styled-component button's template string.

- Added media query for when on 768px screens or bigger:

@media (min-width: 768px) {
width: auto;
}

## Using CSS Modules

CSS modules are only available to projects that are configured to support it. Because it needs a code transformation that need to be done before the code gets to the browser.

React projects created with create-react-app are already configured to support CSS Modules.

- use import React from "react"; and
  import styles from "./Button.module.css"; for a JSX style return block.
- change css file name to "Button.module.css" adding .module in there.

This is a signal to the underlying compilation process to transform the code so that CSS Modules work.

We use the imported styles where we apply our className for the button element in the JSX. In a dynamic block, we use className={styles.button}. The styles object holds the classes we declared in the Button.module.css file in it's namespace.

## Dynamic Styles with CSS Modules

Let's convert CourseInput back to JSX.

- import styles from "./CourseInput.module.css";
- change <FormControl/> to a regular <div>
- add <div className={styles["form-control"]}>using this syntax to access properties because the dash(-) is invalid with the other dot(.) syntax.

The "invalid" style is not yet applied.
For it to be applied we need to make sure that the invalid CSS class is added on the element. We can go back to the back-tick syntax to create a string where we inject values.

<div
  className={`${styles["form-control"]} ${!isValid && styles.invalid}`}
>

To add media queries:

- in Button.module.css add media query with .selector

@media (min-width: 768px) {
.button {
width: auto;
}
}

No other changes required because the media query is on the .button class that is already on the <button> as className={styles.button} from the imported styles from CSS module namespace.

## SECTION 7: Debugging React Apps

## Module Introduction

Understanding Error Messages

Debugging and Analyzing React Apps

Using the React DevTools

## Understanding React Error Messages

## ## SECTION 8: A Complete Practice Project

## Adding a "User" Component

## Adding a Re-usable "Card" Component

## Adding a Re-usable "Button" Component

## Managing the User Input State

## Adding Validation and Resetting Logic

## Adding User List Component

## Managing a List Of Users via State

Lifting the State to share data from 2 components that dont have access to each other. Lift and hold the state to a common parent component.

const [usersList, setUsersList] = useState([]);

const addUserHandler = (uName, uAge) => {
setUsersList((prevUsersList)=>{
return [...prevUsersList, {name: uName, age: uAge, id: Math.random().toString()}];
});
};

return (

<div>
<AddUser onAddUser={addUserHandler} />
<UsersList users={usersList}/>
</div>
);

## Adding The "ErrorModal" Component

## Managing the Error State

const [error, setError] = useState();

if (
enteredUsername.trim().length === 0 ||
enteredAge.trim().length === 0 ||
!usernameIsValid
) {
setError({
title: "Invalid input",
message: "Please enter a valid name and age (non-empty values).",
});
setUsernameIsValid(false);
return;
}
if (+enteredAge.trim() < 1 || !ageIsValid) {
setError({
title: "Invalid age",
message: "Please enter a valid age (> 0).",
});
setAgeIsValid(false);
return;
}

{error && (
<ErrorModal title="An error occured!" message="Something went wrong!" />
)}

## ## SECTION 9: Diving Deeper: Working with Fragments, Portals, and "Refs"

## JSX Limitations and Workarounds

React understands arrays of JSX. So, we can:

return [
error && (
<ErrorModal
key="error-modal"
title={error.title}
message={error.message}
onConfirm={errorHandler}
/>
),
<Card className={styles.input} key="add-user-card">

<form onSubmit={addUserHandler}>
<label htmlFor="username">Username</label>
<input
id="username"
type="text"
value={enteredUsername}
onChange={usernameChangeHandler}
></input>
<label htmlFor="age">Age (Years)</label>
<input
id="age"
type="number"
value={enteredAge}
onChange={ageChangeHandler}
></input>
<Button type="submit">Add User</Button>
</form>
</Card>,
];

## Creating a Wrapper Component

Make custom component that returns props.children. Wrap JSX return block in this "wrapper" component.

Eliminates excessive <div> wrappers, that clutter the actual DOM and slow the browser.

## React Fragments

"<React.Fragment>"
or in some project setups, shortcut "<></>"

return (
<>
<AddUser onAddUser={addUserHandler} />
<UsersList users={usersList} />
</>
);

## Introducing React Portals

React Portals, like Fragments, help us write cleaner code.

They allow us to continue writing our JSX as normal but render the elements un-nested... typacally usefful for when we need to have code top-most so that it can be interpreted by a screen reader.

## Working with Portals

import ReactDOM from "react-dom";

const Backdrop = (props) => {
return <div className={styles.backdrop} onClick={props.onConfirm} />;
};

const ModalOverlay = (props) => {
return (
<Card className={styles.modal}>

<header className={styles.header}>
<h2>{props.title}</h2>
</header>
<div className={styles.content}>
<p>{props.message}</p>
</div>
<footer className={styles.actions}>
<Button onClick={props.onConfirm}>Okay</Button>
</footer>
</Card>
);
};

const ErrorModal = (props) => {
return (
<React.Fragment>
{ReactDOM.createPortal(
<Backdrop onConfirm={props.onConfirm} />,
document.getElementById("backdrop-root")
)}
{ReactDOM.createPortal(
<ModalOverlay
          title={props.title}
          message={props.message}
          onConfirm={props.onConfirm}
        />,
document.getElementById("overlay-root")
)}
</React.Fragment>
);

## Working with "ref"s

const nameInputRef = useRef();
const ageInputRef = useRef();

<input id="age" type="number" ref={ageInputRef}>

Saves the whole DOM element and all properties of the ref'd element when called.

## Controlled Vs. Uncontrolled Components

Once we used:
nameInputRef.current.value = "";
ageInputRef.current.value = "";

The state of the <input>s being referenced became "uncontrolled" by React.
We did not use React to change the value property and so React has no idea that the input field cleared and the state is now blank, changed.

We generally try to AVOID THIS by using useState to keep everything managed by React.

## ## SECTION 10: Advanced: Handling Side Effects, Using Reducers, and Using the Context API

## What are "Side Effects" and Introducing useEffect

The useEffect Hook is called with 2 parameters:

- A function that should be executed AFTER every component evaluation IF the specified dependencies changed.

- Dependencies of this effect - the function only runs if the dependecies changed. An array full of dependencies... and whenever such a dependency changes, that first function will be run.

## Using the useEffect() Hook

Called in function that runs when button is clicked:
localStorage.setItem("isLoggedIn", "1");

useEffect(() => {
const storedUserLoggedInInfo = localStorage.getItem("isLoggedIn");

    if (storedUserLoggedInInfo === "1") {
      setIsLoggedIn(true);
    }

}, []);

## useEffect and Dependencies

useEffect(() => {
setFormIsValid(
enteredEmail.includes("@") && enteredPassword.trim().length > 6
);
}, [enteredEmail, enteredPassword]);

After initial render-run, this effect function will re-run if any of the dependecies have changed since the last component render cycle.

If they havent changed, the effect function will not run again.

## What to add & Not to add as Dependencies

Dont add state-updating functions, variables outside the component function's state values, or built-in API methods.

## Using the useEffect Cleanup Function

useEffect(() => {
console.log("Checking form validity!");
setTimeout(() => {
setFormIsValid(
enteredEmail.includes("@") && enteredPassword.trim().length > 6
);
}, 500);

    return () => {
      console.log("CLEANUP");
      clearTimeout(identifier);

    };

}, [enteredEmail, enteredPassword]);

- Cleanup doesnt run before the first side effect execution.
- But Cleanup runs before every further side effect execution.
- We clearTimeout(identifier) before the next function execution so a new setTimeout can begin upon every keystroke entered-input-state change. Note how console.log("Checking form validity!") if we stop typing for 500ms... with data heavy functions like http requests, this technique regulates how often a fetch to the server is made.

## useEffect Summary

useEffect(() => {
console.log("EFFECT RUNNING");
});

- Without a dependecies array, the useEffect runs after every time the Login coponent function runs. This effect function runs AFTER every component render cycle, including the first time the component was mounted... This changes once we add an empty array.

useEffect(() => {
console.log("EFFECT RUNNING");
}, [enteredPassword]);

- Now this function reruns whenever the component is re-evaluated AND this state changed.

useEffect(() => {
console.log("EFFECT RUNNING");

return () => {
console.log("EFFECT CLEANUP");
}

}, [enteredPassword]);

- We also add a cleanup function that will return before the function as a whole reruns, but NOT before the FIRST time it runs. Will also run if the whole component is unmounted from the DOM.

## Introducing useReducers and Reducers In General

Will help us with state management. Like useState but with more flexiblities and especially useful for more complex state.

For example, multiple states that kind of belong together, that are managing the same thing just different aspects of it.

We SHOULD NOT use one state to set another state like we do in the input validators:
const emailChangeHandler = (event) => {
setEnteredEmail(event.target.value);

    setFormIsValid(
      event.target.value.includes("@") && enteredPassword.trim().length > 6
    );

};

We should use the function form of setting a state-updating function BUT it wont work because with this we only get the lastest state for that state which we are setting. We also are already violating the rule of not seeting one state with another.

This is a scenario where useReducer is always a good choice.

## Using the useReducer() Hook

- const [emailState, dispatchEmail] = useReducer(emailReducer, {
  value: "",
  isValid: null,
  });

- const emailReducer = (state, action) => {
  if (action.type === "USER_INPUT") {
  return { value: action.val, isValid: action.val.includes("@") };
  }
  if (action.type === "INPUT_BLUR") {
  return { value: state.value, isValid: state.value.includes("@") };
  }

  return { value: "", isValid: false };
  };

- const emailChangeHandler = (event) => {
  dispatchEmail({ type: "USER_INPUT", val: event.target.value });

      setFormIsValid(event.target.value.includes("@") && passwordState.isValid);

  };

- const passwordChangeHandler = (event) => {
  dispatchPassword({ type: "USER_INPUT", val: event.target.value });

      setFormIsValid(emailState.isValid && event.target.value.trim().length > 6);

  };

- const validateEmailHandler = () => {
  dispatchEmail({ type: "INPUT_BLUR" });
  };

- const submitHandler = (event) => {
  event.preventDefault();
  props.onLogin(emailState.value, passwordState.value);
  };

- return (
  <Card className={classes.login}>
  <form onSubmit={submitHandler}>
  <div
  className={`${classes.control} ${ emailState.isValid === false ? classes.invalid : "" }`} >
  <label htmlFor="email">E-Mail</label>
  <input
             type="email"
             id="email"
             value={emailState.value}
             onChange={emailChangeHandler}
             onBlur={validateEmailHandler}
           />
  </div>
  <div
  className={`${classes.control} ${ passwordState.isValid === false ? classes.invalid : "" }`} >
  <label htmlFor="password">Password</label>
  <input
             type="password"
             id="password"
             value={passwordState.value}
             onChange={passwordChangeHandler}
             onBlur={validatePasswordHandler}
           />
  </div>
  <div className={classes.actions}>
  <Button type="submit" className={classes.btn} disabled={!formIsValid}>
  Login
  </Button>
  </div>
  </form>
  </Card>
  );

## useReducer & useEffect

const { isValid: emailIsValid } = emailState;
const { isValid: passwordIsValid } = passwordState;

useEffect(() => {
const identifier = setTimeout(() => {
console.log("Checking for validity!");
setFormIsValid(emailIsValid && passwordIsValid);
}, 500);

    return () => {
      console.log("CLEANUP");
      clearTimeout(identifier);
    };

}, [emailIsValid, passwordIsValid]);

## Adding Nested Properties As Dependencies To useEffect

In the previous lecture, we used object destructuring to add object properties as dependencies to useEffect().

const { someProperty } = someObject;
useEffect(() => {
// code that only uses someProperty ...
}, [someProperty]);
This is a very common pattern and approach, which is why I typically use it and why I show it here (I will keep on using it throughout the course).

I just want to point out, that they key thing is NOT that we use destructuring but that we pass specific properties instead of the entire object as a dependency.

We could also write this code and it would work in the same way.

useEffect(() => {
// code that only uses someProperty ...
}, [someObject.someProperty]);
This works just fine as well!

But you should avoid this code:

useEffect(() => {
// code that only uses someProperty ...
}, [someObject]);
Why?

Because now the effect function would re-run whenever ANY property of someObject changes - not just the one property (someProperty in the above example) our effect might depend on.

## useReducer Vs. useState for State Management

## Introducing React Context (Context API)

## Using the React Context API

store/auth-context.js
import React from "react";

React.createContext();

- Takes a default state, usually an object.
  const AuthContext = React.createContext({
  isLoggedIn: false,
  });
  export default AuthContext;

- What we get back will be a component... or an object that also contains will contain components.

To use Context in our App we need to do 2 things:

- You need to "Provide" it... all components that are wrapped by it should have access to it.
  return (
  <AuthContext.Provider>
  <MainHeader isAuthenticated={isLoggedIn} onLogout={logoutHandler} />
  <main>
  {!isLoggedIn && <Login onLogin={loginHandler} />}
  {isLoggedIn && <Home onLogout={logoutHandler} />}
  </main>
  </AuthContext.Provider>
  );

- Besides providing, we need to "Consume" it. Hook into it. Listen to it.

To get access to our value, which at the moment is our default "false" and isnt set up to change, we need to listen... We can "Listen" in 2 ways, AuthContext consumer or by using a React Hook.

- AuthContext-Consumer:

  - import AuthContext
  - Wrap components where we need the data from AuthContext with the Consumer.
  - The consumer takes a child which should be a function with a parameter that is our Context data.
  - Add our JSX to this function body which now has access to our Context data object.

const Navigation = (props) => {
return (
<AuthContext>
{(ctx) => {
return (

<nav className={classes.nav}>
<ul>
{ctx.isLoggedIn && (
<li>
<a href="/">Users</a>
</li>
)}
{props.isLoggedIn && (
<li>
<a href="/">Admin</a>
</li>
)}
{props.isLoggedIn && (
<li>
<button onClick={props.onLogout}>Logout</button>
</li>
)}
</ul>
</nav>
);
}}
</AuthContext>
);
};

This crashes because we do have a default value but our default value will only be used if we Consumed without having a Provider... Technically you dont need it Provider if you have a default value. However you should memorize this pattern because in reality we will use Context to have a value which can change... and that will only be possible with a Provider.

- To Make sure it doesnt crash:
- On the Provider component we can add a "value" prop. Must be named "value".

<AuthContext.Provider
value={{
        isLoggedIn: isLoggedIn,
      }} >

Now, this value object will be updated by React whenever the isLoggedIn changes.
That new context object will be passed down to all the listening components... to all components where we Consume this Context... The difference is that we dont need to forward a prop. Instead we just set it on the provider and then everywhere, in all the child components, we can listen to that.

## Tapping Into Context with the useContext Hook

import React, { useContext } from "react";

const Navigation = (props) => {

const ctx = useContext(AuthContext);

return (

<nav className={classes.nav}>
<ul>
{ctx.isLoggedIn && (
<li>
<a href="/">Users</a>
</li>
)}

## Making Context Dynamic

Using useContext to not just pass data but also functions... to avoid prop chaining functions.

Just pass the data or function through the AuthContext.Provider "value" object. Every listening component will be able to utilize.

## Building & Using a Custom Context Provider Component

import React, { useState, useEffect } from "react";

- const AuthContext = React.createContext({
  isLoggedIn: false,
  onLogout: () => {},
  onLogin: (email, password) => {},
  });

  export const AuthContextProvider = (props) => {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  useEffect(() => {
  const storedUserLoggedInInfo = localStorage.getItem("isLoggedIn");

      if (storedUserLoggedInInfo === "1") {
        setIsLoggedIn(true);
      }

  }, []);

  const logoutHandler = () => {
  localStorage.setItem("isLoggedIn", "1");

      setIsLoggedIn(false);

  };

  const loginHandler = () => {
  localStorage.removeItem("isLoggedIn");

      setIsLoggedIn(true);

  };

  return (
  <AuthContext.Provider
  value={{
          isLoggedIn: isLoggedIn,
          onLogout: logoutHandler,
          onLogin: loginHandler,
        }} >
  {props.children}
  </AuthContext.Provider>
  );
  };

  export default AuthContext;

- ReactDOM.render(
  <AuthContextProvider>
  <App />
  </AuthContextProvider>,
  document.getElementById("root")
  );

## React Context Limitations

## Learning the "Rules of Hooks"

## Refactoring an Input Component

## Diving into "Forward Refs"

- Allows us to interact with the Input Components imperatively... not by passing some state to it that then changes something in the Component, but by calling a function inside of a Component.

  First we removed the "disabled" prop from the <Button> in Login.js to make it clickable when !formIsValid.

  Second, in the submitHandler, since the button is clickable, we want to check if the formIsValid and only if it is do we call authCtx.onLogin(emailState.value, passwordState.value).

  Otherwise (else if {!emailIsValid}), we want to focus on the first invalid input we find... put the cursor into the email input field.

  Or (else), if the email is valid then it has to be the password thats not valid.

- How do we focus the inputs?

  For a regular input, that would be possible by putting a ref on it and then calling the focus method on it.

  example:

  - In the Input Component where we have the native input, we could use the useRef Hook to create a const inputRef = useRef();
  - And then to focus it after the component was rendered, we could use useEffect to run some code after because we learned that the function we pass to useEffect() runs after the component render cycle. If we only want to run it once, when the component initially renders, we pass an empty [] array as a dependencies array, so nothing can change and wont re-run the useEffect side effect.
    useEffect(() => {},[]);
  - We could focus the input by adding the "ref" prop to the input element in JSX. The ref prop is supported on all built-in HTML elements... point at ref={inputRef} and in useEffect function we could now use inputRef.current.focus().
  - useEffect(() => {
    inputRef.current.focus();
    }, []);

We've connected our ref to the input and the used useEffect to focus the input after this component rendered... since the <input> will render for the email and the password, this code will end focused on the password input, the last on rendered.

Our goal is not to do this after the input has rendered.

- For our example we want to have our own method in the Input Component, "activate", and in there we want to use the inputRef.current.focus() imperative command.
- Now the goal is to have activate be called from outside the Input.js. This is a rare scenario because typically, we dont want to code our React projects like this. Instead we want to work with props and state and pass data down to a component to then change something there... But in rare cases like in this example, it might be a more elegant way of focussing this input.

- We want to be able to call focus or activate on our Input Component so that we can use it like the built-in <input> where we have a focus method as well...
- In the Login Component, where we have our custom Inputs, we simply use useRef here as well.
- In our Login Component we create our
  const emailInputRef = useRef();
  const passwordInputRef = useRef();
- Add the "ref" props on the Inputs and point to these.

We have a reference to our own Input components now. Therefore,

- In the submitHandler... if the (!emailIsValid) {
  emailInputRef.current.activate();
  } ... which is the function we have in our Input.js.
- Same for (!passwordIsValid)

If we save this it will not work though... Function components can not be given refs. We're not using props.ref anywhere in Input.js. And ref is a reserved word.

However, we can make this work. we just need to do 2 things.

- In the Input.js we need to import another hook, the useImperativeHandle hook. It's a hook that allows us to use this Component or functionalities from inside this Component imperatively... Not throught the regular state props management, not by controlling the component through state in the parent component, but instead by directly calling or manipulating something in the component programatically.
  Again it's something we rarely want to use.
- We need to call useImperativeHandle() and pass 2 things to it.

  - The 2nd parameter is a function that should return an object and that object will contain all the data we will be able to use from outside. We could add a "focus" field and point at the internal function or variable that should be accessible from outside throught that "focus" name. We point at activate function.

  const activate = () => {
  inputRef.current.focus();
  };

  useImperativeHandle(ref, () => {
  return {
  focus: activate,
  };
  });

- The 1st argument we need to provide to use useImperativeHandle is something we actually get access to in our Component function parameters. Thus far we've always just worked with props but there is a 2nd parameter we can accept, ref!
  This ref is available if a ref is set from outside... So if the parent component, Login, sets a ref on it's use of <Input> and binds it to something, the ref parameter will establish the connection for sharing that data.
  And it is this ref which we should pass to useImperativeHandle

- In order to enable the 2nd parameter, ref, for the Input function component, we need to export it in a special way. We need to wrap it in React.forwardRef().
  It's a method we execute by passing in our whole Component function as the methods 1st parameter.
  React.forwardRef returns a React component that is capable of being bound to a ref.

- In the Login.js we can access the Input ref values and call our imperative function to focus.
  const submitHandler = (event) => {
  event.preventDefault();
  if (formIsValid) {
  authCtx.onLogin(emailState.value, passwordState.value);
  } else if (!emailIsValid) {
  emailInputRef.current.focus();
  } else {
  passwordInputRef.current.focus();
  }
  };

With useImperativeHandle and forwardRef, we can expose functionalities from a React component to it's parent component to then use our component in the parent component through refs and trigger certain functionalities.
Doesnt just work for functions, we could also expose te value throught refs.

## SECTION 11: Practice Project: Building a Food Order App

## Module Introduction

## Adding a Cart Reducer

## Working with Refs & Forward Refs

## Outputting Cart Items

## Working on a More Complex Reducer Logic

## Making Items Removable

## SECTION 12: A Look Behind The Scenes Of React & Optimization Techniques

## Preventing Unnecessary Re-Evaluations with Raect.memo()

## Preventing Function Re-Creation with useCallback();

const toggleParagraphHandler = useCallback(() => {
setShowParagraph((prevShowParagraph) => !prevShowParagraph);
}, []);

## useCallback() and its Dependencies

const toggleParagraphHandler = useCallback(() => {
if (allowToggle) {
setShowParagraph((prevShowParagraph) => !prevShowParagraph);
}
}, [allowToggle]);

const allowToggleHandler = () => {
setAllowToggle(true);
};

## Understanding State Scheduling & Batching

Using prevState with the function form of setting state is recommended if we're depending on the previous state.

## Optimizing with useMemo()

Similar to useCallback to store a function... allows you to store a data block which you dont need re-evaluated.

const DemoList = (props) => {
const sortedList = useMemo(() => {
return props.items.sort((a,b) => a - b);
}, [props.items]);
}

## SECTION 12: A Look Behind The Scenes Of React & Optimization Techniques

## Adding a First Class-based Component

import { Component } from "react";

import classes from "./User.module.css";

class User extends Component {
render() {
return <li className={classes.user}>{this.props.name}</li>;
}
}

// const User = (props) => {
// return <li className={classes.user}>{props.name}</li>;
// };

export default User;

## Working with State & Events

class Users extends Component {
constructor() {
this.state = {
showUsers: true,
moreState: "Test",
};
}

toggleUsersHandler() {
// this.state.showUsers = false;
this.setState((curState) => {
return { showUsers: !curState.showUsers };
});
}

setState merges the new state with the old state. Unlike in functional components using useState() where the updating function replaces the whole state object.

## Introducing Error Boundaries

## SECTION 14: Sending Http Requests (e.g. Connecting to a Database)

## Handling Http Errors

import React, { useState } from "react";

import MoviesList from "./components/MoviesList";
import "./App.css";

function App() {
const [error, setError] = useState(null);
const [movies, setMovies] = useState([]);
const [isLoading, setIsLoading] = useState(false);

async function fetchMoviesHandler() {
setIsLoading(true);
setError(null);

    try {
      const response = await fetch("https://swapi.dev/api/films/");
      if (!response.ok) {
        throw new Error("Something went wrong!");
      }
      const data = await response.json();

      const transformedMovies = data.results.map((movieData) => {
        return {
          id: movieData.episode_id,
          title: movieData.title,
          openingText: movieData.opening_crawl,
          releaseDate: movieData.release_date,
        };
      });
      setMovies(transformedMovies);
    } catch (error) {
      setError(error.message);
    }
    setIsLoading(false);

}

let content = <p>Found no movies.</p>;

if (movies.length > 0) {
content = <MoviesList movies={movies} />;
}

if (error) {
content = <p>{error}</p>;
}

if (isLoading) {
content = <p>Loading...</p>;
}

return (
<React.Fragment>

<section>
<button onClick={fetchMoviesHandler}>Fetch Movies</button>
</section>
<section>
{
content /_ {!isLoading && movies.length > 0 && <MoviesList movies={movies} />}
{!isLoading && movies.length === 0 && !error && <p>Found no movies.</p>}
{isLoading && <p>Loading...</p>}
{!isLoading && error && <p>{error}</p>} _/
}
</section>
</React.Fragment>
);
}

export default App;

## Using useEffect() For Requests

function App() {
const [error, setError] = useState(null);
const [movies, setMovies] = useState([]);
const [isLoading, setIsLoading] = useState(false);

const fetchMoviesHandler = useCallback(async () => {
setIsLoading(true);
setError(null);

    try {
      const response = await fetch("https://swapi.dev/api/films/");
      if (!response.ok) {
        throw new Error("Something went wrong!");
      }
      const data = await response.json();

      const transformedMovies = data.results.map((movieData) => {
        return {
          id: movieData.episode_id,
          title: movieData.title,
          openingText: movieData.opening_crawl,
          releaseDate: movieData.release_date,
        };
      });
      setMovies(transformedMovies);
    } catch (error) {
      setError(error.message);
    }
    setIsLoading(false);

}, []);

useEffect(() => {
fetchMoviesHandler();
}, [fetchMoviesHandler]);

## Preparing The project For The Next Steps

Firebase => Realtime Database

## Sending a POST Request

async function addMovieHandler(movie) {
const response = await fetch(
"https://react-http-18691-default-rtdb.firebaseio.com/movies.json",
{
method: "POST",
body: JSON.stringify(movie),
headers: {
"Content-Type": "application/json",
},
}
);
const data = await response.json();
console.log(data);
}

## SECTION 15: Building Custom React Hooks

## Creating a Custom React Hook Function

import {useState, useEffect} from 'react';

const useCounter = () => {
const [counter, setCounter] = useState(0);

useEffect(() => {
const interval = setInterval(() => {
setCounter((prevCounter) => prevCounter + 1);
}, 1000);

    return () => clearInterval(interval);

}, []);
};

export default useCounter;

## Using Custom Hooks

import Card from "./Card";
import useCounter from "../hooks/use-counter";

const ForwardCounter = () => {
const counter = useCounter();

return <Card>{counter}</Card>;
};

export default ForwardCounter;

## Configuring Custom Hooks

import { useState, useEffect } from "react";

const useCounter = (forwards = true) => {
const [counter, setCounter] = useState(0);

useEffect(() => {
const interval = setInterval(() => {
if (forwards) {
setCounter((prevCounter) => prevCounter + 1);
} else {
setCounter((prevCounter) => prevCounter - 1);
}
}, 1000);

    return () => clearInterval(interval);

}, [forwards]);

return counter;
};

export default useCounter;

## Building a Custom Http Hook

import { useState } from "react";

const useHttp = (requestConfig, applyData) => {
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);

const sendRequest = async (taskText) => {
setIsLoading(true);
setError(null);
try {
const response = await fetch(requestConfig.url, {
method: requestConfig.method ? requestConfig.method : "GET",
headers: requestConfig.headers ? requestConfig.headers : {},
body: requestConfig.body ? JSON.stringify(requestConfig.body) : null,
});

      if (!response.ok) {
        throw new Error("Request failed!");
      }

      const data = await response.json();

      applyData(data);
    } catch (err) {
      setError(err.message || "Something went wrong!");
    }
    setIsLoading(false);

};
return {
isLoading,
error,
sendRequest,
};
};

export default useHttp;

## Using a Custom Http Hook

import React, { useEffect, useState } from "react";

import Tasks from "./components/Tasks/Tasks";
import NewTask from "./components/NewTask/NewTask";
import useHttp from "./hooks/use-http";

function App() {
const [tasks, setTasks] = useState([]);

const transformTasks = (tasksObj) => {
const loadedTasks = [];

    for (const taskKey in tasksObj) {
      loadedTasks.push({ id: taskKey, text: tasksObj[taskKey].text });
    }

    setTasks(loadedTasks);

};

const {
isLoading,
error,
sendRequest: fetchTasks,
} = useHttp(
{
url: "https://react-example-7f53a-default-rtdb.firebaseio.com/tasks.json",
},
transformTasks
);

// const fetchTasks = async (taskText) => {
// setIsLoading(true);
// setError(null);
// try {
// const response = await fetch(
// "https://react-example-7f53a-default-rtdb.firebaseio.com/tasks.json"
// );

// if (!response.ok) {
// throw new Error("Request failed!");
// }

// const data = await response.json();

// const loadedTasks = [];

// for (const taskKey in data) {
// loadedTasks.push({ id: taskKey, text: data[taskKey].text });
// }

// setTasks(loadedTasks);
// } catch (err) {
// setError(err.message || "Something went wrong!");
// }
// setIsLoading(false);
// };

useEffect(() => {
fetchTasks();
}, []);

const taskAddHandler = (task) => {
setTasks((prevTasks) => prevTasks.concat(task));
};

return (
<React.Fragment>
<NewTask onAddTask={taskAddHandler} />
<Tasks
        items={tasks}
        loading={isLoading}
        error={error}
        onFetch={fetchTasks}
      />
</React.Fragment>
);
}

export default App;

## Adjusting the Custom Hook Logic

import { useCallback, useState } from "react";

const useHttp = (applyData) => {
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);

const sendRequest = useCallback(
async (requestConfig) => {
setIsLoading(true);
setError(null);
try {
const response = await fetch(requestConfig.url, {
method: requestConfig.method ? requestConfig.method : "GET",
headers: requestConfig.headers ? requestConfig.headers : {},
body: requestConfig.body ? JSON.stringify(requestConfig.body) : null,
});

        if (!response.ok) {
          throw new Error("Request failed!");
        }

        const data = await response.json();

        applyData(data);
      } catch (err) {
        setError(err.message || "Something went wrong!");
      }
      setIsLoading(false);
    },
    [applyData]

);

return {
isLoading,
error,
sendRequest,
};
};

export default useHttp;

import React, { useCallback, useEffect, useState } from "react";

import Tasks from "./components/Tasks/Tasks";
import NewTask from "./components/NewTask/NewTask";
import useHttp from "./hooks/use-http";

function App() {
const [tasks, setTasks] = useState([]);

const transformTasks = useCallback((tasksObj) => {
const loadedTasks = [];

    for (const taskKey in tasksObj) {
      loadedTasks.push({ id: taskKey, text: tasksObj[taskKey].text });
    }

    setTasks(loadedTasks);

}, []);

const { isLoading, error, sendRequest: fetchTasks } = useHttp(transformTasks);

useEffect(() => {
fetchTasks({
url: "https://react-example-7f53a-default-rtdb.firebaseio.com/tasks.json",
});
}, [fetchTasks]);

const taskAddHandler = (task) => {
setTasks((prevTasks) => prevTasks.concat(task));
};

return (
<React.Fragment>
<NewTask onAddTask={taskAddHandler} />
<Tasks
        items={tasks}
        loading={isLoading}
        error={error}
        onFetch={fetchTasks}
      />
</React.Fragment>
);
}

export default App;

## Using The Custom Hook In More Components (FULL)

## App.js

import React, { useEffect, useState } from "react";

import Tasks from "./components/Tasks/Tasks";
import NewTask from "./components/NewTask/NewTask";
import useHttp from "./hooks/use-http";

function App() {
const [tasks, setTasks] = useState([]);

const { isLoading, error, sendRequest: fetchTasks } = useHttp();

useEffect(() => {
const transformTasks = (tasksObj) => {
const loadedTasks = [];

      for (const taskKey in tasksObj) {
        loadedTasks.push({ id: taskKey, text: tasksObj[taskKey].text });
      }

      setTasks(loadedTasks);
    };

    fetchTasks(
      {
        url: "https://react-example-7f53a-default-rtdb.firebaseio.com/tasks.json",
      },
      transformTasks
    );

}, [fetchTasks]);

const taskAddHandler = (task) => {
setTasks((prevTasks) => prevTasks.concat(task));
};

return (
<React.Fragment>
<NewTask onAddTask={taskAddHandler} />
<Tasks
        items={tasks}
        loading={isLoading}
        error={error}
        onFetch={fetchTasks}
      />
</React.Fragment>
);
}

export default App;

## useHttp.js

import { useCallback, useState } from "react";

const useHttp = () => {
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);

const sendRequest = useCallback(async (requestConfig, applyData) => {
setIsLoading(true);
setError(null);
try {
const response = await fetch(requestConfig.url, {
method: requestConfig.method ? requestConfig.method : "GET",
headers: requestConfig.headers ? requestConfig.headers : {},
body: requestConfig.body ? JSON.stringify(requestConfig.body) : null,
});

      if (!response.ok) {
        throw new Error("Request failed!");
      }

      const data = await response.json();

      applyData(data);
    } catch (err) {
      setError(err.message || "Something went wrong!");
    }
    setIsLoading(false);

}, []);

return {
isLoading,
error,
sendRequest,
};
};

export default useHttp;

## import Section from "../UI/Section";

import TaskForm from "./TaskForm";
import useHttp from "../../hooks/use-http";

const NewTask = (props) => {
const { isLoading, error, sendRequest: sendTaskRequest } = useHttp();

const createTask = (taskText, taskData) => {
const generatedId = taskData.name; // firebase-specific => "name" contains generated id
const createdTask = { id: generatedId, text: taskText };
props.onAddTask(createdTask);
};

const enterTaskHandler = (taskText) => {
sendTaskRequest(
{
url: "https://react-example-7f53a-default-rtdb.firebaseio.com/tasks.json",
method: "POST",
headers: {
"Content-Type": "application/json",
},
body: { text: taskText },
},
createTask.bind(null, taskText)
);
};

return (

<Section>
<TaskForm onEnterTask={enterTaskHandler} loading={isLoading} />
{error && <p>{error}</p>}
</Section>
);
};

export default NewTask;

## SECTION 16: Working with Forms and User Input

## What's So Complex About Forms?

Can have many different states.

## Dealing With Form Submission & Getting User Input Values

## Adding A Custom Input Hook

## use-input.js

import { useState } from "react";

const useInput = (validateValue) => {
const [enteredValue, setEnteredValue] = useState("");
const [isTouched, setIsTouched] = useState(false);

const valueIsValid = validateValue(enteredValue);
const hasError = !valueIsValid && isTouched;

const valueChangeHandler = (e) => {
setEnteredValue(e.target.value);
};

const inputBlurHandler = () => {
setIsTouched(true);
};

const reset = () => {
setEnteredValue("");
setIsTouched(false);
};

return {
value: enteredValue,
isValid: valueIsValid,
hasError,
valueChangeHandler,
inputBlurHandler,
reset,
};
};

export default useInput;

## SimpleInput.js

// import { useState } from "react";

import useInput from "../hooks/use-input";

const SimpleInput = (props) => {
const {
value: enteredName,
isValid: enteredNameIsValid,
hasError: nameInputHasError,
valueChangeHandler: nameChangeHandler,
inputBlurHandler: nameBlurHandler,
reset: resetNameInput,
} = useInput((value) => value.trim() !== "");

const {
value: enteredEmail,
isValid: enteredEmailIsValid,
hasError: emailInputHasError,
valueChangeHandler: emailChangeHandler,
inputBlurHandler: emailBlurHandler,
reset: resetEmailInput,
} = useInput((value) => value.trim().includes("@"));

// const [enteredName, setEnteredName] = useState("");
// const [enteredNameTouched, setEnteredNameTouched] = useState(false);

// const [enteredEmail, setEnteredEmail] = useState("");
// const [enteredEmailTouched, setEnteredEmailTouched] = useState(false);

// const enteredNameIsValid = enteredName.trim() !== "";
// const nameInputIsInvalid = !enteredNameIsValid && enteredNameTouched;

// const enteredEmailIsValid =
// enteredEmail.trim() !== "" && enteredEmail.includes("@");
// const emailInputIsInvalid = !enteredEmailIsValid && enteredEmailTouched;

let formIsValid = false;

if (enteredNameIsValid && enteredEmailIsValid) {
formIsValid = true;
}

const formSubmitHandler = (e) => {
e.preventDefault();

    // setEnteredNameTouched(true);
    // setEnteredEmailTouched(true);

    if (!enteredNameIsValid || !enteredEmailIsValid) {
      return;
    }

    console.log(enteredName);
    console.log(enteredEmail);

    // setEnteredName("");
    // setEnteredNameTouched(false);
    resetNameInput();

    // setEnteredEmail("");
    // setEnteredEmailTouched(false);
    resetEmailInput();

};

const nameInputClass = nameInputHasError
? "form-control invalid"
: "form-control";
const emailInputClass = emailInputHasError
? "form-control invalid"
: "form-control";

return (

<form onSubmit={formSubmitHandler}>
<div className={nameInputClass}>
<label htmlFor="name">Your Name</label>
<input
          type="text"
          id="name"
          onChange={nameChangeHandler}
          onBlur={nameBlurHandler}
          value={enteredName}
        />
{nameInputHasError && <p>Name must not be empty.</p>}
</div>
<div className={emailInputClass}>
<label htmlFor="email">Your Email</label>
<input
          type="email"
          id="email"
          onChange={emailChangeHandler}
          onBlur={emailBlurHandler}
          value={enteredEmail}
        />
{emailInputHasError && <p>Email must not be empty.</p>}
</div>
<div className="form-actions">
<button disabled={!formIsValid}>Submit</button>
</div>
</form>
);
};

export default SimpleInput;

## Applying Our Hook And Knowledge To A New Form

import useBasic from "../hooks/use-basic";

const BasicForm = (props) => {
const {
value: enteredFirstName,
isValid: enteredFirstNameIsValid,
hasError: firstNameInputHasError,
valueChangeHandler: firstNameChangeHandler,
inputBlurHandler: firstNameBlurHandler,
reset: resetFirstNameInput,
} = useBasic((value) => value.trim() !== "");

const {
value: enteredLastName,
isValid: enteredLastNameIsValid,
hasError: lastNameInputHasError,
valueChangeHandler: lastNameChangeHandler,
inputBlurHandler: lastNameBlurHandler,
reset: resetLastNameInput,
} = useBasic((value) => value.trim() !== "");

const {
value: enteredEmail,
isValid: enteredEmailIsValid,
hasError: emailInputHasError,
valueChangeHandler: emailChangeHandler,
inputBlurHandler: emailBlurHandler,
reset: resetEmailInput,
} = useBasic((value) => value.trim().includes("@"));

let formIsValid = false;

if (
enteredFirstNameIsValid &&
enteredLastNameIsValid &&
enteredEmailIsValid
) {
formIsValid = true;
}

const formSubmitHandler = (e) => {
e.preventDefault();

    if (!formIsValid) {
      return;
    }

    console.log("Submitted!");
    console.log(enteredFirstName);
    console.log(enteredLastName);
    console.log(enteredEmail);

    resetFirstNameInput();
    resetLastNameInput();
    resetEmailInput();

};

const firstNameInputClass = firstNameInputHasError
? "form-control invalid"
: "form-control";
const lastNameInputClass = lastNameInputHasError
? "form-control invalid"
: "form-control";
const emailInputClass = emailInputHasError
? "form-control invalid"
: "form-control";

return (

<form onSubmit={formSubmitHandler}>
<div className="control-group">
<div className={firstNameInputClass}>
<label htmlFor="firstname">First Name</label>
<input
            type="text"
            id="firstname"
            onChange={firstNameChangeHandler}
            onBlur={firstNameBlurHandler}
            value={enteredFirstName}
          />
{firstNameInputHasError && (
<p className="error-text">First Name must not be empty.</p>
)}
</div>
<div className={lastNameInputClass}>
<label htmlFor="lastname">Last Name</label>
<input
            type="text"
            id="lastname"
            onChange={lastNameChangeHandler}
            onBlur={lastNameBlurHandler}
            value={enteredLastName}
          />
{lastNameInputHasError && (
<p className="error-text">Last Name must not be empty.</p>
)}
</div>
<div className={emailInputClass}>
<label htmlFor="email">E-Mail Address</label>
<input
            type="email"
            id="email"
            onChange={emailChangeHandler}
            onBlur={emailBlurHandler}
            value={enteredEmail}
          />
{emailInputHasError && (
<p className="error-text">Email must not be empty.</p>
)}
</div>
</div>
<div className="form-actions">
<button disabled={!formIsValid}>Submit</button>
</div>
</form>
);
};

export default BasicForm;

## Bonus: Using useReducer()

import { useReducer } from "react";

const initialInputState = {
value: "",
isTouched: false,
};

const inputStateReducer = (state, action) => {
if (action.type === "INPUT") {
return { value: action.value, isTouched: state.isTouched };
}
if (action.type === "BLUR") {
return { isTouched: true, value: state.value };
}
if (action.type === "RESET") {
return { isTouched: false, value: "" };
}
return inputStateReducer;
};

const useInput = (validateValue) => {
const [inputState, dispatch] = useReducer(
inputStateReducer,
initialInputState
);

const valueIsValid = validateValue(inputState.value);
const hasError = !valueIsValid && inputState.isTouched;

const valueChangeHandler = (e) => {
dispatch({ type: "INPUT", value: e.target.value });
};

const inputBlurHandler = () => {
dispatch({ type: "BLUR" });
};

const reset = () => {
dispatch({ type: "RESET" });
};

return {
value: inputState.value,
isValid: valueIsValid,
hasError,
valueChangeHandler,
inputBlurHandler,
reset,
};
};

export default useInput;

## SECTION 17: Practice Project: Adding Http & Forms To The Food Order App

## Moving "Meals" Data To The Backend

{
"m1": {
"description": "Finest fish and veggies",
"name": "Sushi",
"price": 22.99
},
"m2": {
"description": "A german specialty!",
"name": "Schnitzel",
"price": 16.5
},
"m3": {
"description": "American, raw, meaty",
"name": "Barbecue Burger",
"price": 12.99
},
"m4": {
"description": "Healthy...and green...",
"name": "Green Bowl",
"price": 18.99
}
}

import { useEffect, useState } from "react";

import Card from "../UI/Card";
import MealItem from "./MealItem/MealItem";
import classes from "./AvailableMeals.module.css";

const AvailableMeals = () => {
const [meals, setMeals] = useState([]);

useEffect(() => {
const fetchMeals = async () => {
const response = await fetch(
"https://react-example-7f53a-default-rtdb.firebaseio.com/meals.json"
);
const responseData = await response.json();
console.log(responseData);

      const loadedMeals = [];

      for (const key in responseData) {
        loadedMeals.push({
          id: key,
          name: responseData[key].name,
          description: responseData[key].description,
          price: responseData[key].price,
        });
      }

      setMeals(loadedMeals);
    };

    fetchMeals();

}, []);

const mealsList = meals.map((meal) => (
<MealItem
      key={meal.id}
      id={meal.id}
      name={meal.name}
      description={meal.description}
      price={meal.price}
    />
));

return (

<section className={classes.meals}>
<Card>
<ul>{mealsList}</ul>
</Card>
</section>
);
};

export default AvailableMeals;

## Handling The Loading State

const [isLoading, setIsLoading] = useState(true);

if (isLoading === true) {
return (

<section className={classes.MealsLoading}>
<p>Loading...</p>
</section>
);
}

## Handling Errors

We're using try/catch but keep in mind that fetch meals is an async function and always returns a promise... If we throw an error inside of a promise, taht error will cause that promise to reject. This would warrant us to await this fetchMeals and and in turn have to turn our Effect function into an async function but that IS NOT ALLOWED for React Hooks.

We could work around it by putting the try/catch into a seperate function. One for sending the http request and one for error handling.

Here we will simply use the fact that it's a promise and use the catch() method on it. So instead of try/catch, we want to .catch(err => {}) the error in the catch block and set states according to this error being caught. This is the traditional promise only way of handling an error inside of a promise.

import { useEffect, useState } from "react";

import Card from "../UI/Card";
import MealItem from "./MealItem/MealItem";
import classes from "./AvailableMeals.module.css";

const AvailableMeals = () => {
const [meals, setMeals] = useState([]);
const [isLoading, setIsLoading] = useState(true);
const [httpError, setHttpError] = useState(null);

useEffect(() => {
const fetchMeals = async () => {
const response = await fetch(
"https://react-example-7f53a-default-rtdb.firebaseio.com/meals"
);

      if (!response.ok) {
        throw new Error("Something went wrong!");
      }

      const responseData = await response.json();
      console.log(responseData);

      const loadedMeals = [];

      for (const key in responseData) {
        loadedMeals.push({
          id: key,
          name: responseData[key].name,
          description: responseData[key].description,
          price: responseData[key].price,
        });
      }

      setMeals(loadedMeals);
      setIsLoading(false);
    };

    try {
      fetchMeals();
    } catch (err) {
      setIsLoading(false);
      setHttpError(err.message);
    }

}, []);

if (isLoading === true) {
return (

<section className={classes.MealsLoading}>
<p>Loading...</p>
</section>
);
}

if (httpError) {
return (

<section className={classes.MealsError}>
<p>{httpError}</p>
</section>
);
}

const mealsList = meals.map((meal) => (
<MealItem
      key={meal.id}
      id={meal.id}
      name={meal.name}
      description={meal.description}
      price={meal.price}
    />
));

return (

<section className={classes.meals}>
<Card>
<ul>{mealsList}</ul>
</Card>
</section>
);
};

export default AvailableMeals;

## Adding A Checkout Form

import classes from './Checkout.module.css';

const Checkout = (props) => {
const confirmHandler = (event) => {
event.preventDefault();
};

return (

<form className={classes.form} onSubmit={confirmHandler}>
<div className={classes.control}>
<label htmlFor='name'>Your Name</label>
<input type='text' id='name' />
</div>
<div className={classes.control}>
<label htmlFor='street'>Street</label>
<input type='text' id='street' />
</div>
<div className={classes.control}>
<label htmlFor='postal'>Postal Code</label>
<input type='text' id='postal' />
</div>
<div className={classes.control}>
<label htmlFor='city'>City</label>
<input type='text' id='city' />
</div>
<div className={classes.actions}>
<button type='button' onClick={props.onCancel}>
Cancel
</button>
<button className={classes.submit}>Confirm</button>
</div>
</form>
);
};

export default Checkout;

## Reading Form Values

import { useRef } from "react";

import classes from "./Checkout.module.css";

const Checkout = (props) => {
const nameInputRef = useRef();
const streetInputRef = useRef();
const postalCodeInputRef = useRef();
const cityInputRef = useRef();

const confirmHandler = (event) => {
event.preventDefault();

    const enteredName = nameInputRef.current.value;
    const enteredStreet = streetInputRef.current.value;
    const enteredPostalCode = postalCodeInputRef.current.value;
    const enteredCity = cityInputRef.current.value;

};

return (

<form className={classes.form} onSubmit={confirmHandler}>
<div className={classes.control}>
<label htmlFor="name">Your Name</label>
<input type="text" id="name" ref={nameInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="street">Street</label>
<input type="text" id="street" ref={streetInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="postal">Postal Code</label>
<input type="text" id="postal" ref={postalCodeInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="city">City</label>
<input type="text" id="city" ref={cityInputRef} />
</div>
<div className={classes.actions}>
<button type="button" onClick={props.onCancel}>
Cancel
</button>
<button className={classes.submit}>Confirm</button>
</div>
</form>
);
};

export default Checkout;

## Adding Form Validation

import { useRef, useState } from "react";

import classes from "./Checkout.module.css";

const isEmpty = (value) => value.trim() === "";
const isNotFiveChars = (value) => value.trim().length !== 5;

const Checkout = (props) => {
const [formInputsValidity, setFormInputsValidity] = useState({
name: true,
street: true,
city: true,
postalCode: true,
});

const nameInputRef = useRef();
const streetInputRef = useRef();
const postalCodeInputRef = useRef();
const cityInputRef = useRef();

const confirmHandler = (event) => {
event.preventDefault();

    const enteredName = nameInputRef.current.value;
    const enteredStreet = streetInputRef.current.value;
    const enteredPostalCode = postalCodeInputRef.current.value;
    const enteredCity = cityInputRef.current.value;

    const enteredNameIsValid = !isEmpty(enteredName);
    const enteredStreetIsValid = !isEmpty(enteredStreet);
    const enteredPostalCodeIsValid = !isNotFiveChars(enteredPostalCode);
    const enteredCityIsValid = !isEmpty(enteredCity);

    setFormInputsValidity({
      name: enteredNameIsValid,
      street: enteredStreetIsValid,
      city: enteredCityIsValid,
      postalCode: enteredPostalCodeIsValid,
    });

    const formIsValid =
      enteredNameIsValid &&
      enteredStreetIsValid &&
      enteredPostalCodeIsValid &&
      enteredCityIsValid;

    // Input Feedback

    if (!formIsValid) {
      return;
    }

    // Submit cart data

};

const nameControlClasses = `${classes.control} ${ formInputsValidity.name ? "" : classes.invalid }`;
const streetControlClasses = `${classes.control} ${ formInputsValidity.street ? "" : classes.invalid }`;
const postalCodeControlClasses = `${classes.control} ${ formInputsValidity.postalCode ? "" : classes.invalid }`;
const cityControlClasses = `${classes.control} ${ formInputsValidity.city ? "" : classes.invalid }`;

return (

<form className={classes.form} onSubmit={confirmHandler}>
<div className={nameControlClasses}>
<label htmlFor="name">Your Name</label>
<input type="text" id="name" ref={nameInputRef} />
{!formInputsValidity.name && <p>Please enter a valid name!</p>}
</div>
<div className={streetControlClasses}>
<label htmlFor="street">Street</label>
<input type="text" id="street" ref={streetInputRef} />
{!formInputsValidity.street && <p>Please enter a valid street!</p>}
</div>
<div className={postalCodeControlClasses}>
<label htmlFor="postal">Postal Code</label>
<input type="text" id="postal" ref={postalCodeInputRef} />
{!formInputsValidity.postalCode && (
<p>Please enter a valid postal code (5 characters long)!</p>
)}
</div>
<div className={cityControlClasses}>
<label htmlFor="city">City</label>
<input type="text" id="city" ref={cityInputRef} />
{!formInputsValidity.city && <p>Please enter a valid city!</p>}
</div>
<div className={classes.actions}>
<button type="button" onClick={props.onCancel}>
Cancel
</button>
<button className={classes.submit}>Confirm</button>
</div>
</form>
);
};

export default Checkout;

## Submitting and Sending Cart Data

import { useContext, useState } from "react";

import Modal from "../UI/Modal";
import CartItem from "./CartItem";
import classes from "./Cart.module.css";
import CartContext from "../../store/cart-context";
import Checkout from "./Checkout";

const Cart = (props) => {
const [isCheckout, setIsCheckout] = useState(false);
const cartCtx = useContext(CartContext);

const totalAmount = `$${cartCtx.totalAmount.toFixed(2)}`;
const hasItems = cartCtx.items.length > 0;

const cartItemRemoveHandler = (id) => {
cartCtx.removeItem(id);
};

const cartItemAddHandler = (item) => {
cartCtx.addItem(item);
};

const orderHandler = () => {
setIsCheckout(true);
};

const submitOrderHandler = (userData) => {
fetch(
"https://react-example-7f53a-default-rtdb.firebaseio.com/orders.json",
{
method: "POST",
body: JSON.stringify({
user: userData,
orderedItems: cartCtx.items,
}),
}
);
};

const cartItems = (

<ul className={classes["cart-items"]}>
{cartCtx.items.map((item) => (
<CartItem
key={item.id}
name={item.name}
amount={item.amount}
price={item.price}
onRemove={cartItemRemoveHandler.bind(null, item.id)}
onAdd={cartItemAddHandler.bind(null, item)}
/>
))}
</ul>
);

const modalActions = (

<div className={classes.actions}>
<button className={classes["button--alt"]} onClick={props.onClose}>
Close
</button>
{hasItems && (
<button className={classes.button} onClick={orderHandler}>
Order
</button>
)}
</div>
);

return (
<Modal onClose={props.onClose}>
{cartItems}

<div className={classes.total}>
<span>Total Amount</span>
<span>{totalAmount}</span>
</div>
{isCheckout && (
<Checkout onConfirm={submitOrderHandler} onCancel={props.onClose} />
)}
{!isCheckout && modalActions}
</Modal>
);
};

export default Cart;

## Checkout.js

import { useRef, useState } from "react";

import classes from "./Checkout.module.css";

const isEmpty = (value) => value.trim() === "";
const isNotFiveChars = (value) => value.trim().length !== 5;

const Checkout = (props) => {
const [formInputsValidity, setFormInputsValidity] = useState({
name: true,
street: true,
city: true,
postalCode: true,
});

const nameInputRef = useRef();
const streetInputRef = useRef();
const postalCodeInputRef = useRef();
const cityInputRef = useRef();

const confirmHandler = (event) => {
event.preventDefault();

    const enteredName = nameInputRef.current.value;
    const enteredStreet = streetInputRef.current.value;
    const enteredPostalCode = postalCodeInputRef.current.value;
    const enteredCity = cityInputRef.current.value;

    const enteredNameIsValid = !isEmpty(enteredName);
    const enteredStreetIsValid = !isEmpty(enteredStreet);
    const enteredPostalCodeIsValid = !isNotFiveChars(enteredPostalCode);
    const enteredCityIsValid = !isEmpty(enteredCity);

    setFormInputsValidity({
      name: enteredNameIsValid,
      street: enteredStreetIsValid,
      city: enteredCityIsValid,
      postalCode: enteredPostalCodeIsValid,
    });

    const formIsValid =
      enteredNameIsValid &&
      enteredStreetIsValid &&
      enteredPostalCodeIsValid &&
      enteredCityIsValid;

    // Input Feedback

    if (!formIsValid) {
      return;
    }

    // Submit cart data
    props.onConfirm({
      name: enteredName,
      street: enteredStreet,
      city: enteredCity,
      postalCode: enteredPostalCode,
    });

};

const nameControlClasses = `${classes.control} ${ formInputsValidity.name ? "" : classes.invalid }`;
const streetControlClasses = `${classes.control} ${ formInputsValidity.street ? "" : classes.invalid }`;
const postalCodeControlClasses = `${classes.control} ${ formInputsValidity.postalCode ? "" : classes.invalid }`;
const cityControlClasses = `${classes.control} ${ formInputsValidity.city ? "" : classes.invalid }`;

return (

<form className={classes.form} onSubmit={confirmHandler}>
<div className={nameControlClasses}>
<label htmlFor="name">Your Name</label>
<input type="text" id="name" ref={nameInputRef} />
{!formInputsValidity.name && <p>Please enter a valid name!</p>}
</div>
<div className={streetControlClasses}>
<label htmlFor="street">Street</label>
<input type="text" id="street" ref={streetInputRef} />
{!formInputsValidity.street && <p>Please enter a valid street!</p>}
</div>
<div className={postalCodeControlClasses}>
<label htmlFor="postal">Postal Code</label>
<input type="text" id="postal" ref={postalCodeInputRef} />
{!formInputsValidity.postalCode && (
<p>Please enter a valid postal code (5 characters long)!</p>
)}
</div>
<div className={cityControlClasses}>
<label htmlFor="city">City</label>
<input type="text" id="city" ref={cityInputRef} />
{!formInputsValidity.city && <p>Please enter a valid city!</p>}
</div>
<div className={classes.actions}>
<button type="button" onClick={props.onCancel}>
Cancel
</button>
<button className={classes.submit}>Confirm</button>
</div>
</form>
);
};

export default Checkout;

## Adding Better User Feedback

## SECTION 18: Diving into Redux (An Alternative To The Context API)

## Exploring The Core Redux Concepts

Navigate to folder:

npm init -y
npm i redux

const redux = require("redux");

const counterReducer = (state = { counter: 0 }, action) => {
return {
counter: state.counter + 1,
};
};

const store = redux.createStore(counterReducer);
// console.log(store.getState()); // { counter: 1 }

const counterSubscriber = () => {
const latestState = store.getState();
console.log(latestState);
};

store.subscribe(counterSubscriber);

store.dispatch({ type: "increment" }); // { counter: 2 }
store.dispatch({ type: "increments" }); // { counter: 3 }

Run in terminal:
node redux-demo.js
=>
{ counter: 2 }
{ counter: 3 }

## More Redux Basics

const redux = require("redux");

const counterReducer = (state = { counter: 0 }, action) => {
if (action.type === "increment") {
return {
counter: state.counter + 1,
};
}

if (action.type === "decrement") {
return {
counter: state.counter - 1,
};
}

return state;
};

const store = redux.createStore(counterReducer);
// console.log(store.getState()); // { counter: 0 }

const counterSubscriber = () => {
const latestState = store.getState();
console.log(latestState);
};

store.subscribe(counterSubscriber);

store.dispatch({ type: "increment" });
store.dispatch({ type: "decrement" });

## Preparing A New Project

npm i redux react-redux

## Creating A Redux Store For React

import { createStore } from "redux";

const counterReducer = (state = { counter: 0 }, action) => {
if (action.type === "increment") {
return { counter: state.counter + 1 };
}
if (action.type === "decrement") {
return { counter: state.counter - 1 };
}

return state;
};

const store = createStore(counterReducer);

export default store;

## Providing The Store

import React from "react";
import ReactDOM from "react-dom";
import { Provider } from "react-redux";

import "./index.css";
import App from "./App";
import store from "./store/index";

ReactDOM.render(
<Provider store={store}>
<App />{" "}
</Provider>,
document.getElementById("root")
);

## Using Redux Data In React Components

import { useSelector } from "react-redux";

import classes from "./Counter.module.css";

const Counter = () => {
const counter = useSelector((state) => state.counter);

const toggleCounterHandler = () => {};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
<div className={classes.value}>{counter}</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## Dispatching Actions From Inside Components

import { useSelector, useDispatch } from "react-redux";

import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter);

const incrementHandler = () => {
dispatch({ type: "increment" });
};

const decrementHandler = () => {
dispatch({ type: "decrement" });
};

const toggleCounterHandler = () => {};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
<div className={classes.value}>{counter}</div>
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## Redux with Class-based Components

import { Component } from "react";
import { useSelector, useDispatch, connect } from "react-redux";

import classes from "./Counter.module.css";

class Counter extends Component {
incrementHandler() {
this.props.increment();
}

decrementHandler() {
this.props.decrement();
}

toggleCounterHandler() {}

render() {
return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
<div className={classes.value}>{this.props.counter}</div>
<div>
<button onClick={this.incrementHandler.bind(this)}>Increment</button>
<button onClick={this.decrementHandler.bind(this)}>Decrement</button>
</div>
<button onClick={this.toggleCounterHandler}>Toggle Counter</button>
</main>
);
}
}

const mapStateToProps = (state) => {
return {
counter: state.counter,
};
};

const mapDispatchToProps = (dispatch) => {
return {
increment: () => dispatch({ type: "increment" }),
decrement: () => dispatch({ type: "decrement" }),
};
};

export default connect(mapStateToProps, mapDispatchToProps)(Counter);

## Attaching Payloads To Actions

import { useSelector, useDispatch } from "react-redux";

import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter);

const incrementHandler = () => {
dispatch({ type: "increment" });
};
const increaseHandler = () => {
dispatch({ type: "increase", amount: 10 });
};

const decrementHandler = () => {
dispatch({ type: "decrement" });
};

const toggleCounterHandler = () => {};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
<div className={classes.value}>{counter}</div>
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={increaseHandler}>Increment 10</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## Working With Multiple State Properties

import { useSelector, useDispatch } from "react-redux";

import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter);
const showCounter = useSelector((state) => state.showCounter);

const incrementHandler = () => {
dispatch({ type: "increment" });
};
const increaseHandler = () => {
dispatch({ type: "increase", amount: 10 });
};

const decrementHandler = () => {
dispatch({ type: "decrement" });
};

const toggleCounterHandler = () => {
dispatch({ type: "toggle" });
};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
{showCounter && <div className={classes.value}>{counter}</div>}
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={increaseHandler}>Increment 10</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## How To Work With Redux State Directly

Never mutate state directly. Update state by providing the whole brand new object or array.

## Redux Challenges and Introducing Redux Toolkit

## Adding State Slices

import { createStore } from "redux";
import { createSlice } from "@reduxjs/toolkit";

const initialState = { counter: 0, showCounter: true };

createSlice({
name: 'counter',
initialState,
reducers: {
increment(state){
state.counter++;
},
decrement(state){
state.counter--;
},
increase(state, action){
state.counter = state.counter + action.amount;
},
toggleCounter(state){
state.showCounter = !state.showCounter;
},

    }

});

const counterReducer = (state = initialState, action) => {
if (action.type === "increment") {
return { counter: state.counter + 1, showCounter: state.showCounter };
}
if (action.type === "increase") {
return {
counter: state.counter + action.amount,
showCounter: state.showCounter,
};
}
if (action.type === "decrement") {
return { counter: state.counter - 1, showCounter: state.showCounter };
}

if (action.type === "toggle") {
return {
showCounter: !state.showCounter,
counter: state.counter,
};
}

return state;
};

const store = createStore(counterReducer);

export default store;

## Connecting Redux Toolkit State

import { createStore } from "redux";
import { configureStore, createSlice } from "@reduxjs/toolkit";

const initialState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
name: "counter",
initialState,
reducers: {
increment(state) {
state.counter++;
},
decrement(state) {
state.counter--;
},
increase(state, action) {
state.counter = state.counter + action.amount;
},
toggleCounter(state) {
state.showCounter = !state.showCounter;
},
},
});

const store = configureStore({
reducer: counterSlice.reducer
// reducer: {counter: counterSlice.reducer, ...}
})
// const store = createStore(counterSlice.reducer);

export default store;

## Migrating Everything To Redux Toolkit

import { useSelector, useDispatch } from "react-redux";

import { counterActions } from "../store/index";
import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter);
const showCounter = useSelector((state) => state.showCounter);

const incrementHandler = () => {
dispatch(counterActions.increment());
};
const increaseHandler = () => {
dispatch(counterActions.increase(10)); // { type: SOME_UNIQUE_ID, payload: 10 }
};

const decrementHandler = () => {
dispatch(counterActions.decrement());
};

const toggleCounterHandler = () => {
dispatch(counterActions.toggleCounter());
};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
{showCounter && <div className={classes.value}>{counter}</div>}
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={increaseHandler}>Increment 10</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## .../store index.js

import { configureStore, createSlice } from "@reduxjs/toolkit";

const initialState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
name: "counter",
initialState,
reducers: {
increment(state) {
state.counter++;
},
decrement(state) {
state.counter--;
},
increase(state, action) {
state.counter = state.counter + action.payload;
},
toggleCounter(state) {
state.showCounter = !state.showCounter;
},
},
});

const store = configureStore({
reducer: counterSlice.reducer,
// reducer: {counter: counterSlice.reducer, ...}
});
// const store = createStore(counterSlice.reducer);

export const counterActions = counterSlice.actions;
export default store;

## Working With Multiple Slices

import { Fragment } from "react";

import Counter from "./components/Counter";
import Header from "./components/Header";
import Auth from "./components/Auth";

function App() {
return (
<Fragment>

<Header />
<Auth />
<Counter />
</Fragment>
);
}

export default App;

##

import { configureStore, createSlice } from "@reduxjs/toolkit";

const initialCounterState = { counter: 0, showCounter: true };

const counterSlice = createSlice({
name: "counter",
initialState: initialCounterState,
reducers: {
increment(state) {
state.counter++;
},
decrement(state) {
state.counter--;
},
increase(state, action) {
state.counter = state.counter + action.payload;
},
toggleCounter(state) {
state.showCounter = !state.showCounter;
},
},
});

const initialAuthState = {
isAuthenticated: false,
};
const authSlice = createSlice({
name: "authentication",
initialState: initialAuthState,
reducers: {
login(state) {
state.isAuthenticated = true;
},
logout(state) {
state.isAuthenticated = false;
},
},
});

const store = configureStore({
// reducer: counterSlice.reducer,
reducer: { counter: counterSlice.reducer, auth: authSlice.reducer },
});
// const store = createStore(counterSlice.reducer);

export const counterActions = counterSlice.actions;
export const authActions = authSlice.actions;

export default store;

##

import { useSelector, useDispatch } from "react-redux";

import { counterActions } from "../store/index";
import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter.counter);
const showCounter = useSelector((state) => state.counter.showCounter);

const incrementHandler = () => {
dispatch(counterActions.increment());
};
const increaseHandler = () => {
dispatch(counterActions.increase(10)); // { type: SOME_UNIQUE_ID, payload: 10 }
};

const decrementHandler = () => {
dispatch(counterActions.decrement());
};

const toggleCounterHandler = () => {
dispatch(counterActions.toggleCounter());
};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
{showCounter && <div className={classes.value}>{counter}</div>}
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={increaseHandler}>Increment 10</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

## Reading And Dispatching From A New Slice

import { useSelector, useDispatch } from "react-redux";

import { counterActions } from "../store/index";
import classes from "./Counter.module.css";

const Counter = () => {
const dispatch = useDispatch();
const counter = useSelector((state) => state.counter.counter);
const showCounter = useSelector((state) => state.counter.showCounter);

const incrementHandler = () => {
dispatch(counterActions.increment());
};
const increaseHandler = () => {
dispatch(counterActions.increase(10)); // { type: SOME_UNIQUE_ID, payload: 10 }
};

const decrementHandler = () => {
dispatch(counterActions.decrement());
};

const toggleCounterHandler = () => {
dispatch(counterActions.toggleCounter());
};

return (

<main className={classes.counter}>
<h1>Redux Counter</h1>
{showCounter && <div className={classes.value}>{counter}</div>}
<div>
<button onClick={incrementHandler}>Increment</button>
<button onClick={increaseHandler}>Increment 10</button>
<button onClick={decrementHandler}>Decrement</button>
</div>
<button onClick={toggleCounterHandler}>Toggle Counter</button>
</main>
);
};

export default Counter;

##

import { Fragment } from "react";
import { useSelector } from "react-redux";

import Counter from "./components/Counter";
import Header from "./components/Header";
import Auth from "./components/Auth";
import UserProfile from "./components/UserProfile";

function App() {
const isAuth = useSelector((state) => state.auth.isAuthenticated);

return (
<Fragment>

<Header />
{!isAuth && <Auth />}
{isAuth && <UserProfile />}
<Counter />
</Fragment>
);
}

export default App;

##

import { useSelector, useDispatch } from "react-redux";

import classes from "./Header.module.css";
import { authActions } from "../store/index";

const Header = () => {
const dispatch = useDispatch();

const logoutHandler = (event) => {
dispatch(authActions.logout());
};

const isAuth = useSelector((state) => state.auth.isAuthenticated);

return (

<header className={classes.header}>
<h1>Redux Auth</h1>
{isAuth && (
<nav>
<ul>
<li>
<a href="/">My Products</a>
</li>
<li>
<a href="/">My Sales</a>
</li>
<li>
<button onClick={logoutHandler}>Logout</button>
</li>
</ul>
</nav>
)}
</header>
);
};

export default Header;

##

import { useDispatch } from "react-redux";
import classes from "./Auth.module.css";
import { authActions } from "../store/index";

const Auth = () => {
const dispatch = useDispatch();

const loginHandler = (event) => {
event.preventDefault();

    dispatch(authActions.login());

};

return (

<main className={classes.auth}>
<section>
<form onSubmit={loginHandler}>
<div className={classes.control}>
<label htmlFor="email">Email</label>
<input type="email" id="email" />
</div>
<div className={classes.control}>
<label htmlFor="password">Password</label>
<input type="password" id="password" />
</div>
<button>Login</button>
</form>
</section>
</main>
);
};

export default Auth;

## Splitting Our Code

## Advanced Redux

## Redux and Side Effects (and Asynchronous Code)

## Refresher / Practice: Part 1/2

> > Set up UI slice with redux

import { createSlice } from "@reduxjs/toolkit";

const uiSlice = createSlice({
name: "ui",
initialState: { cartIsVisible: false },
reducers: {
toggle(state) {
state.cartIsVisible = !state.cartIsVisible;
},
},
});

export const uiActions = uiSlice.actions;

export default uiSlice;

> > Set up index.js store with redux

import { configureStore } from "@reduxjs/toolkit";
import uiSlice from "./ui-slice";

const store = configureStore({
reducer: { ui: uiSlice.reducer },
});

export default store;

> > Now we need to provide it to the Application for it to have an effect.

import ReactDOM from "react-dom";
import { Provider } from "react-redux";
import store from "./store/index";

import "./index.css";
import App from "./App";

ReactDOM.render(
<Provider store={store}>
<App />
</Provider>,
document.getElementById("root")
);

> > Dispatch action from store. Set up My Cart button to dispatch onClick with useDispatch Hook.

import { uiActions } from "../../store/ui-slice";
import { useDispatch } from "react-redux";

import classes from "./CartButton.module.css";

const CartButton = (props) => {
const dispatch = useDispatch();
const toggleCartHandler = (event) => {
event.preventDefault();
dispatch(uiActions.toggle());
};
return (
<button className={classes.button} onClick={toggleCartHandler}>
<span>My Cart</span>
<span className={classes.badge}>1</span>
</button>
);
};

export default CartButton;

> > Take advantage of the onClick dispatch changing the state of uiSlice's state.cartIsVisible. Go to the App component because that's where we render the Cart. Extracting state from redux with useSelector Hook.

import { useSelector } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";

function App() {
const showCart = useSelector((state) => state.ui.cartIsVisible);
return (
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
);
}

export default App;

> > Managing content of the Cart: Set up cart slice.

import { createSlice } from "@reduxjs/toolkit";

createSlice({
name: "cart",
initialState: {
items: [],
totalQuantity: 0,
},
reducers: {
addItemToCart(state, action) {
const newItem = action.payload;
const existingItem = state.items.find((item) => item.id === newItem.id);
if (!existingItem) {
state.items.push({
itemId: newItem.id,
price: newItem.price,
quantity: 1,
totalPrice: newItem.price,
name: newItem.title,
});
} else {
existingItem.quantity++;
existingItem.totalPrice = totalPrice + newItem.price;
}
},
removeItemFromCart() {},
},
});

#

import { configureStore } from "@reduxjs/toolkit";
import uiSlice from "./ui-slice";
import cartSlice from "./cart-slice";

const store = configureStore({
reducer: { ui: uiSlice.reducer, cart: cartSlice.reducer },
});

export default store;

#

import { useSelector } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";

function App() {
const showCart = useSelector((state) => state.ui.cartIsVisible);
return (
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
);
}

export default App;

#

import ProductItem from "./ProductItem";
import classes from "./Products.module.css";

const DUMMY_PRODUCTS = [
{
id: "p1",
price: 6,
title: "My First Book",
description: "The first book I ever wrote.",
},
{
id: "p2",
price: 5,
title: "My Second Book",
description: "The second book I ever wrote.",
},
];

const Products = (props) => {
return (

<section className={classes.products}>
<h2>Buy your favorite products</h2>
<ul>
{DUMMY_PRODUCTS.map((product) => (
<ProductItem
            key={product.id}
            id={product.id}
            title={product.title}
            price={product.price}
            description={product.description}
          />
))}
</ul>
</section>
);
};

#

export default Products;
import { useDispatch } from "react-redux";

import { cartActions } from "../../store/cart-slice";
import Card from "../UI/Card";
import classes from "./ProductItem.module.css";

const ProductItem = (props) => {
const { title, price, description, id } = props;
const dispatch = useDispatch();

const addToCartHandler = () => {
dispatch(
cartActions.addItemToCart({
id: id,
title: title,
price: price,
})
);
};

return (

<li className={classes.item}>
<Card>
<header>
<h3>{title}</h3>
<div className={classes.price}>${price.toFixed(2)}</div>
</header>
<p>{description}</p>
<div className={classes.actions}>
<button onClick={addToCartHandler}>Add to Cart</button>
</div>
</Card>
</li>
);
};

export default ProductItem;

#

import { createSlice } from "@reduxjs/toolkit";

const cartSlice = createSlice({
name: "cart",
initialState: {
items: [],
totalQuantity: 0,
},
reducers: {
addItemToCart(state, action) {
const newItem = action.payload;
const existingItem = state.items.find((item) => item.id === newItem.id);
state.totalQuantity++;
if (!existingItem) {
state.items.push({
itemId: newItem.id,
price: newItem.price,
quantity: 1,
totalPrice: newItem.price,
name: newItem.title,
});
} else {
existingItem.quantity++;
existingItem.totalPrice = existingItem.totalPrice + newItem.price;
}
},
removeItemFromCart(state, action) {
const id = action.payload;
const existingItem = state.items.find((item) => item.id === id);
state.totalQuantity--;
if (existingItem.quantity === 1) {
state.items = state.items.filter((item) => item.id !== id);
} else {
existingItem.quantity--;
existingItem.totalPrice = existingItem.totalPrice - existingItem.price;
}
},
},
});

export const cartActions = cartSlice.actions;
export default cartSlice;

## Redux & Async Code

Goal is to store the add or remove from cart state change in a backend store and bring the current cart to the frontend on request.

NO ASYNC or side effect code inside of reducers. Reducers must be pure.

## Frontend Code vs Backend Code

We're trying to transform the data to the format the backend will need and send it to the backend without doing that sending inside of the reducer.
Where to put our logic?

## Where To Put Our Logic

We're trying to transform the data to the format the backend will need and send it to the backend without doing that sending inside of the reducer.
Where to put our logic?

## Using useEffect with Redux

import { useDispatch } from "react-redux";

import { cartActions } from "../../store/cart-slice";
import Card from "../UI/Card";
import classes from "./ProductItem.module.css";

const ProductItem = (props) => {
const { title, price, description, id } = props;
const dispatch = useDispatch();

const addToCartHandler = () => {
dispatch(
cartActions.addItemToCart({
id: id,
title: title,
price: price,
})
);
};

return (

<li className={classes.item}>
<Card>
<header>
<h3>{title}</h3>
<div className={classes.price}>${price.toFixed(2)}</div>
</header>
<p>{description}</p>
<div className={classes.actions}>
<button onClick={addToCartHandler}>Add to Cart</button>
</div>
</Card>
</li>
);
};

export default ProductItem;

##

import { useEffect } from "react";
import { useSelector } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";

function App() {
const showCart = useSelector((state) => state.ui.cartIsVisible);
const cart = useSelector((state) => state.cart);

useEffect(() => {
fetch("https://react-http-18691-default-rtdb.firebaseio.com/cart.json", {
method: "PUT",
body: JSON.stringify(cart),
});
}, [cart]);
return (
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
);
}

export default App;

## Handling HTTP States and Feedback with Redux

import { createSlice } from "@reduxjs/toolkit";

const uiSlice = createSlice({
name: "ui",
initialState: { cartIsVisible: false, notification: null },
reducers: {
toggle(state) {
state.cartIsVisible = !state.cartIsVisible;
},
showNotification(state, action) {
state.notification = {
status: action.payload.status,
title: action.payload.title,
message: action.payload.message,
};
},
},
});

export const uiActions = uiSlice.actions;

export default uiSlice;

##

import classes from "./Notification.module.css";

const Notification = (props) => {
let specialClasses = "";

if (props.status === "error") {
specialClasses = classes.error;
}
if (props.status === "success") {
specialClasses = classes.success;
}

const cssClasses = `${classes.notification} ${specialClasses}`;

return (

<section className={cssClasses}>
<h2>{props.title}</h2>
<p>{props.message}</p>
</section>
);
};

export default Notification;

##

import { Fragment, useEffect } from "react";
import { useSelector, useDispatch } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";
import Notification from "./components/UI/Notification";
import { uiActions } from "./store/ui-slice";

let isInitial = true;

function App() {
const dispatch = useDispatch();
const showCart = useSelector((state) => state.ui.cartIsVisible);
const cart = useSelector((state) => state.cart);
const notification = useSelector((state) => state.ui.notification);

useEffect(() => {
const sendCartData = async () => {
dispatch(
uiActions.showNotification({
status: "pending",
title: "Sending...",
message: "Sending cart data!",
})
);
const response = await fetch(
"https://react-http-18691-default-rtdb.firebaseio.com/cart.json",
{
method: "PUT",
body: JSON.stringify(cart),
}
);

      if (!response.ok) {
        throw new Error("Sending cart data failed.");
      }

      dispatch(
        uiActions.showNotification({
          status: "success",
          title: "Success!",
          message: "Sent cart data successfully!",
        })
      );
    };

    if (isInitial) {
      isInitial = false;
      return;
    }

    sendCartData().catch((err) => {
      dispatch(
        uiActions.showNotification({
          status: "error",
          title: "Error!",
          message: "Sending cart data failed!",
        })
      );
    });

}, [cart, dispatch]);

return (
<Fragment>
{notification && (
<Notification
          status={notification.status}
          title={notification.title}
          message={notification.message}
        />
)}
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
</Fragment>
);
}

export default App;

## Using An Action Creator Thunk

import { createSlice } from "@reduxjs/toolkit";
import { uiActions } from "./ui-slice";

const cartSlice = createSlice({
name: "cart",
initialState: {
items: [],
totalQuantity: 0,
},
reducers: {
addItemToCart(state, action) {
const newItem = action.payload;
const existingItem = state.items.find((item) => item.id === newItem.id);
state.totalQuantity++;
if (!existingItem) {
state.items.push({
id: newItem.id,
price: newItem.price,
quantity: 1,
totalPrice: newItem.price,
name: newItem.title,
});
} else {
existingItem.quantity++;
existingItem.totalPrice = existingItem.totalPrice + newItem.price;
}
},
removeItemFromCart(state, action) {
const id = action.payload;
const existingItem = state.items.find((item) => item.id === id);
state.totalQuantity--;
if (existingItem.quantity === 1) {
state.items = state.items.filter((item) => item.id !== id);
} else {
existingItem.quantity--;
existingItem.totalPrice = existingItem.totalPrice - existingItem.price;
}
},
},
});

export const sendCartData = (cart) => {
return async (dispatch) => {
dispatch(
uiActions.showNotification({
status: "pending",
title: "Sending...",
message: "Sending cart data!",
})
);

    const sendRequest = async () => {
      const response = await fetch(
        "https://react-http-18691-default-rtdb.firebaseio.com/cart.json",
        {
          method: "PUT",
          body: JSON.stringify(cart),
        }
      );

      if (!response.ok) {
        throw new Error("Sending cart data failed.");
      }
    };

    try {
      await sendRequest();

      dispatch(
        uiActions.showNotification({
          status: "success",
          title: "Success!",
          message: "Sent cart data successfully!",
        })
      );
    } catch (err) {
      dispatch(
        uiActions.showNotification({
          status: "error",
          title: "Error!",
          message: "Sending cart data failed!",
        })
      );
    }

};
};

export const cartActions = cartSlice.actions;
export default cartSlice;

##

import { Fragment, useEffect } from "react";
import { useSelector, useDispatch } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";
import Notification from "./components/UI/Notification";
import { sendCartData } from "./store/cart-slice";

let isInitial = true;

function App() {
const dispatch = useDispatch();
const showCart = useSelector((state) => state.ui.cartIsVisible);
const cart = useSelector((state) => state.cart);
const notification = useSelector((state) => state.ui.notification);

useEffect(() => {
if (isInitial) {
isInitial = false;
return;
}

    dispatch(sendCartData(cart));

}, [cart, dispatch]);

return (
<Fragment>
{notification && (
<Notification
          status={notification.status}
          title={notification.title}
          message={notification.message}
        />
)}
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
</Fragment>
);
}

export default App;

## Getting Started with Fetching Data

## Finalizing the Fetching Logic

import { createSlice } from "@reduxjs/toolkit";

const cartSlice = createSlice({
name: "cart",
initialState: {
items: [],
totalQuantity: 0,
changed: false,
},
reducers: {
replaceCart(state, action) {
state.totalQuantity = action.payload.totalQuantity;
state.items = action.payload.items;
},
addItemToCart(state, action) {
const newItem = action.payload;
const existingItem = state.items.find((item) => item.id === newItem.id);
state.totalQuantity++;
state.changed = true;
if (!existingItem) {
state.items.push({
id: newItem.id,
price: newItem.price,
quantity: 1,
totalPrice: newItem.price,
name: newItem.title,
});
} else {
existingItem.quantity++;
existingItem.totalPrice = existingItem.totalPrice + newItem.price;
}
},
removeItemFromCart(state, action) {
const id = action.payload;
const existingItem = state.items.find((item) => item.id === id);
state.totalQuantity--;
state.changed = true;
if (existingItem.quantity === 1) {
state.items = state.items.filter((item) => item.id !== id);
} else {
existingItem.quantity--;
existingItem.totalPrice = existingItem.totalPrice - existingItem.price;
}
},
},
});

export const cartActions = cartSlice.actions;
export default cartSlice;

##

import { uiActions } from "./ui-slice";
import { cartActions } from "./cart-slice";

export const fetchCartData = () => {
return async (dispatch) => {
const fetchData = async () => {
const response = await fetch(
"https://react-http-18691-default-rtdb.firebaseio.com/cart.json"
);

      if (!response.ok) {
        throw new Error("Could not fetch cart data!");
      }

      const data = await response.json();
      return data;
    };
    try {
      const cartData = await fetchData();
      dispatch(
        cartActions.replaceCart({
          items: cartData.items || [],
          totalQuantity: cartData.totalQuantity,
        })
      );
    } catch (err) {
      dispatch(
        uiActions.showNotification({
          status: "error",
          title: "Error!",
          message: "Fetching cart data failed!",
        })
      );
    }

};
};

export const sendCartData = (cart) => {
return async (dispatch) => {
dispatch(
uiActions.showNotification({
status: "pending",
title: "Sending...",
message: "Sending cart data!",
})
);

    const sendRequest = async () => {
      const response = await fetch(
        "https://react-http-18691-default-rtdb.firebaseio.com/cart.json",
        {
          method: "PUT",
          body: JSON.stringify({
            items: cart.items,
            totalQuantity: cart.totalQuantity,
          }),
        }
      );

      if (!response.ok) {
        throw new Error("Sending cart data failed.");
      }
    };

    try {
      await sendRequest();

      dispatch(
        uiActions.showNotification({
          status: "success",
          title: "Success!",
          message: "Sent cart data successfully!",
        })
      );
    } catch (err) {
      dispatch(
        uiActions.showNotification({
          status: "error",
          title: "Error!",
          message: "Sending cart data failed!",
        })
      );
    }

};
};

##

import { Fragment, useEffect } from "react";
import { useSelector, useDispatch } from "react-redux";

import Cart from "./components/Cart/Cart";
import Layout from "./components/Layout/Layout";
import Products from "./components/Shop/Products";
import Notification from "./components/UI/Notification";
import { sendCartData, fetchCartData } from "./store/cart-actions";

let isInitial = true;

function App() {
const dispatch = useDispatch();
const showCart = useSelector((state) => state.ui.cartIsVisible);
const cart = useSelector((state) => state.cart);
const notification = useSelector((state) => state.ui.notification);

useEffect(() => {
dispatch(fetchCartData());
}, [dispatch]);

useEffect(() => {
if (isInitial) {
isInitial = false;
return;
}

    if (cart.changed) {
      dispatch(sendCartData(cart));
    }

}, [cart, dispatch]);

return (
<Fragment>
{notification && (
<Notification
          status={notification.status}
          title={notification.title}
          message={notification.message}
        />
)}
<Layout>
{showCart && <Cart />}
<Products />
</Layout>
</Fragment>
);
}

export default App;

## Exploring the Redux DevTools

Chrome Extension.

## ## SECTION 20: Building a Multi-Page SPA with React Router

## What Is Routing And Why?

We want websites where we have different paths so that when the URL changes, we load different pages.
Usually we make this happen with different .html pages we have ready in our server.
This requires us to leave the browser, request a new page, and wait for that page to load... not the Raect style.
We can continue building a SPA with one .html request and response.
We can then manipulate dom by handling URL changes with the client-side (React) code.
There's a 3rd-party package for this client-side routing.

## Installing React Router

npm i react-router-dom

## Defining and Using Routes

import ReactDOM from "react-dom";
import { BrowserRouter } from "react-router-dom";

import "./index.css";
import App from "./App";

ReactDOM.render(
<BrowserRouter>
<App />
</BrowserRouter>,
document.getElementById("root")
);

##

import { Route } from "react-router-dom";

import Welcome from "./pages/Welcome";
import Products from "./pages/Products";

function App() {
return (

<div>
<Route path="/welcome">
<Welcome />
</Route>
<Route path="/products">
<Products />
</Route>
</div>
);
}

export default App;

##

const Welcome = () => {
return <h1>The Welcome Page.</h1>;
};

export default Welcome;

##

const Products = () => {
return <h1>The Products Page.</h1>;
};

export default Products;

## Working with Links

import { Link } from "react-router-dom";

const MainHeader = () => {
return (

<header>
<nav>
<ul>
<li>
<Link to="/welcome">Welcome</Link>
</li>
<li>
<Link to="/products">Products</Link>
</li>
</ul>
</nav>
</header>
);
};

export default MainHeader;

## Using NavLinks

import { NavLink } from "react-router-dom";

import classes from "./MainHeader.module.css";

const MainHeader = () => {
return (

<header className={classes.header}>
<nav>
<ul>
<li>
<NavLink activeClassName={classes.active} to="/welcome">
Welcome
</NavLink>
</li>
<li>
<NavLink activeClassName={classes.active} to="/products">
Products
</NavLink>
</li>
</ul>
</nav>
</header>
);
};

export default MainHeader;

## Adding Dynamic Routes with Params

import { Route } from "react-router-dom";

import Welcome from "./pages/Welcome";
import Products from "./pages/Products";
import MainHeader from "./components/MainHeader";
import ProductDetail from "./pages/ProductDetail";

function App() {
return (

<div>
<MainHeader />
<main>
<Route path="/welcome">
<Welcome />
</Route>
<Route path="/products">
<Products />
</Route>
<Route path="/product-detail/:productId">
<ProductDetail />
</Route>
</main>
</div>
);
}

export default App;

## Extracting Route Params

import { useParams } from "react-router";

const ProductDetail = () => {
const params = useParams();

console.log(params.productId);

return (

<section>
<h1>Product Detail</h1>
<p>{params.productId}</p>
</section>
);
};

export default ProductDetail;

## Using "Switch" and "exact" For Configuring Routes

import { Route, Switch } from "react-router-dom";

import Welcome from "./pages/Welcome";
import Products from "./pages/Products";
import MainHeader from "./components/MainHeader";
import ProductDetail from "./pages/ProductDetail";

function App() {
return (

<div>
<MainHeader />
<main>
<Switch>
<Route path="/welcome">
<Welcome />
</Route>
<Route path="/products" exact>
<Products />
</Route>
<Route path="/products/:productId">
<ProductDetail />
</Route>
</Switch>
</main>
</div>
);
}

export default App;

##

import { Link } from "react-router-dom";

const Products = () => {
return (

<section>
<h1>The Products Page.</h1>
<ul>
<li>
<Link to="/products/p1">A Book</Link>
</li>
<li>
<Link to="/products/p2">A Carpet</Link>
</li>
<li>
<Link to="/products/p3">An Online Course</Link>
</li>
</ul>
</section>
);
};

export default Products;

## Working with Nested Routes

import { Route } from "react-router";

const Welcome = () => {
return (

<section>
<h1>The Welcome Page</h1>
<Route path="/welcome/new-user">
<p>Welcome, new user!</p>
</Route>
</section>
);
};

export default Welcome;

## Redirecting The Use

import { Route, Switch, Redirect } from "react-router-dom";

import Welcome from "./pages/Welcome";
import Products from "./pages/Products";
import MainHeader from "./components/MainHeader";
import ProductDetail from "./pages/ProductDetail";

function App() {
return (

<div>
<MainHeader />
<main>
<Switch>
<Route path="/" exact>
<Redirect to="/welcome" />
</Route>
<Route path="/welcome">
<Welcome />
</Route>
<Route path="/products" exact>
<Products />
</Route>
<Route path="/products/:productId">
<ProductDetail />
</Route>
</Switch>
</main>
</div>
);
}

export default App;

## Time to Practice: Onwards to a New Project

## Practice Redirecting & Extracting Params

## Practicing Nested Routes

import { Fragment } from "react";
import { Route, useParams } from "react-router-dom";

import Comments from "../components/comments/Comments";

const QuoteDetail = () => {
const params = useParams();

console.log(params.quoteId);

return (
<Fragment>

<h1>Quote Detail Page</h1>
<p>{params.quoteId}</p>
<Route path={`/quotes/${params.quoteId}/:comments`}>
<Comments />
</Route>
</Fragment>
);
};

export default QuoteDetail;

## Adding a Layout Wropper Component

import { NavLink } from "react-router-dom";
import classes from "./MainNavigation.module.css";

const MainNavigation = () => {
return (

<header className={classes.header}>
<div className={classes.logo}>Great Quotes</div>
<nav className={classes.nav}>
<ul>
<li>
<NavLink to="/quotes" activeClassName={classes.active}>
All Quotes
</NavLink>
</li>
<li>
<NavLink to="/new-quote" activeClassName={classes.active}>
Add a Quote
</NavLink>
</li>
</ul>
</nav>
</header>
);
};

export default MainNavigation;

##

import { Fragment } from "react";
import MainNavigation from "./MainNavigation";
import classes from "./Layout.module.css";

const Layout = (props) => {
return (
<Fragment>
<MainNavigation />

<main className={classes.main}>{props.children}</main>
</Fragment>
);
};

export default Layout;

##

import { Route, Switch, Redirect} from "react-router-dom";

import AllQuotes from "./pages/AllQuotes";
import QuoteDetail from "./pages/QuoteDetail";
import NewQuote from "./pages/NewQuote";
import Layout from "./components/layout/Layout";

function App() {
return (
<Layout>
<Switch>
<Route path="/" exact>
<Redirect to="/quotes" />
</Route>
<Route path="/quotes" exact>
<AllQuotes />
</Route>
<Route path="/quotes/:quoteId">
<QuoteDetail />
</Route>
<Route path="/new-quote">
<NewQuote />
</Route>
</Switch>
</Layout>
);
}

export default App;

## Adding Dummy Data & More Content

import QuoteList from "../components/quotes/QuoteList";

const DUMMY_QUOTES = [
{ id: "q1", author: "Max", text: "Learning React is fun!" },
{ id: "q2", author: "Chris", text: "Learning React is great!" },
];

const AllQuotes = () => {
return <QuoteList quotes={DUMMY_QUOTES} />;
};

export default AllQuotes;

##

import { Fragment } from 'react';

import QuoteItem from './QuoteItem';
import classes from './QuoteList.module.css';

const QuoteList = (props) => {
return (
<Fragment>

<ul className={classes.list}>
{props.quotes.map((quote) => (
<QuoteItem
            key={quote.id}
            id={quote.id}
            author={quote.author}
            text={quote.text}
          />
))}
</ul>
</Fragment>
);
};

export default QuoteList;

## Outputting Data on the "Details" Page

import { Fragment } from "react";
import { Route, useParams } from "react-router-dom";

import Comments from "../components/comments/Comments";
import HighlightedQuote from "../components/quotes/HighlightedQuote";

const DUMMY_QUOTES = [
{ id: "q1", author: "Max", text: "Learning React is fun!" },
{ id: "q2", author: "Chris", text: "Learning React is great!" },
];

const QuoteDetail = () => {
const params = useParams();

const quote = DUMMY_QUOTES.find((quote) => quote.id === params.quoteId);

if (!quote) {
return <p>No Quote Found!</p>;
}

return (
<Fragment>
<HighlightedQuote text={quote.text} author={quote.author} />
<Route path={`/quotes/${params.quoteId}/:comments`}>
<Comments />
</Route>
</Fragment>
);
};

export default QuoteDetail;

##

import classes from './HighlightedQuote.module.css';

const HighlightedQuote = (props) => {
return (

<figure className={classes.quote}>
<p>{props.text}</p>
<figcaption>{props.author}</figcaption>
</figure>
);
};

export default HighlightedQuote;

## Adding a "Not Found" Page

const NotFound = () => {
return (

<div className="centered">
<p>Page not found!</p>
</div>
);
};

export default NotFound;

##

import { Route, Switch, Redirect } from "react-router-dom";

import AllQuotes from "./pages/AllQuotes";
import QuoteDetail from "./pages/QuoteDetail";
import NewQuote from "./pages/NewQuote";
import Layout from "./components/layout/Layout";
import NotFound from "./pages/NotFound";

function App() {
return (
<Layout>
<Switch>
<Route path="/" exact>
<Redirect to="/quotes" />
</Route>
<Route path="/quotes" exact>
<AllQuotes />
</Route>
<Route path="/quotes/:quoteId">
<QuoteDetail />
</Route>
<Route path="/new-quote">
<NewQuote />
</Route>
<Route path="*">
<NotFound />
</Route>
</Switch>
</Layout>
);
}

export default App;

## Implementing Programmatic (Imperative) Navigation

import { useHistory } from "react-router-dom";
import QuoteForm from "../components/quotes/QuoteForm";

const NewQuote = () => {
const history = useHistory();

const addQuoteHandler = (quoteData) => {
console.log(quoteData);

    history.push("/quotes");

};

return <QuoteForm onAddQuote={addQuoteHandler} />;
};

export default NewQuote;

## Preventing Possibly Unwanted Route Transitions with the "Prompt"

import { Fragment, useRef, useState } from "react";
import { Prompt } from "react-router-dom";

import Card from "../UI/Card";
import LoadingSpinner from "../UI/LoadingSpinner";
import classes from "./QuoteForm.module.css";

const QuoteForm = (props) => {
const [isEntering, setIsEntering] = useState(false);

const authorInputRef = useRef();
const textInputRef = useRef();

function submitFormHandler(event) {
event.preventDefault();

    const enteredAuthor = authorInputRef.current.value;
    const enteredText = textInputRef.current.value;

    // optional: Could validate here

    props.onAddQuote({ author: enteredAuthor, text: enteredText });

}

const finishEnteringHandler = () => {
setIsEntering(false);
};

const formFocusHandler = () => {
setIsEntering(true);
};

return (
<Fragment>
<Prompt
when={isEntering}
message={(location) =>
"Are you sure you want to leave? All your entered data will be lost!"
}
/>
<Card>

<form
          onFocus={formFocusHandler}
          className={classes.form}
          onSubmit={submitFormHandler}
        >
{props.isLoading && (
<div className={classes.loading}>
<LoadingSpinner />
</div>
)}

          <div className={classes.control}>
            <label htmlFor="author">Author</label>
            <input type="text" id="author" ref={authorInputRef} />
          </div>
          <div className={classes.control}>
            <label htmlFor="text">Text</label>
            <textarea id="text" rows="5" ref={textInputRef}></textarea>
          </div>
          <div className={classes.actions}>
            <button onClick={finishEnteringHandler} className="btn">
              Add Quote
            </button>
          </div>
        </form>
      </Card>
    </Fragment>

);
};

export default QuoteForm;

## Working With Query Parameters

import { Fragment } from "react";
import { useHistory, useLocation } from "react-router-dom";

import QuoteItem from "./QuoteItem";
import classes from "./QuoteList.module.css";

const sortQuotes = (quotes, ascending) => {
return quotes.sort((quoteA, quoteB) => {
if (ascending) {
return quoteA.id > quoteB.id ? 1 : -1;
} else {
return quoteA.id < quoteB.id ? 1 : -1;
}
});
};

const QuoteList = (props) => {
const history = useHistory();
const location = useLocation();

const queryParams = new URLSearchParams(location.search);

const isSortingAscending = queryParams.get("sort") === "asc";

const sortedQuotes = sortQuotes(props.quotes, isSortingAscending);

const changeSortingHandler = () => {
history.push("/quotes?sort=" + (isSortingAscending ? "desc" : "asc"));
};

return (
<Fragment>

<div className={classes.sorting}>
<button onClick={changeSortingHandler}>
Sort {isSortingAscending ? "Descending" : "Ascending"}
</button>
</div>
<ul className={classes.list}>
{sortedQuotes.map((quote) => (
<QuoteItem
            key={quote.id}
            id={quote.id}
            author={quote.author}
            text={quote.text}
          />
))}
</ul>
</Fragment>
);
};

export default QuoteList;

## Getting Creative With Nested Routes

import { Fragment } from "react";
import { Link, Route, useParams } from "react-router-dom";

import Comments from "../components/comments/Comments";
import HighlightedQuote from "../components/quotes/HighlightedQuote";

const DUMMY_QUOTES = [
{ id: "q1", author: "Max", text: "Learning React is fun!" },
{ id: "q2", author: "Chris", text: "Learning React is great!" },
];

const QuoteDetail = () => {
const params = useParams();

const quote = DUMMY_QUOTES.find((quote) => quote.id === params.quoteId);

if (!quote) {
return <p>No Quote Found!</p>;
}

return (
<Fragment>
<HighlightedQuote text={quote.text} author={quote.author} />

      <Route path={`/quotes/${params.quoteId}`} exact>
        <div className="centered">
          <Link className="btn--flat" to={`/quotes/${params.quoteId}/comments`}>
            Load Comments
          </Link>
        </div>
      </Route>

      <Route path={`/quotes/${params.quoteId}/:comments`}>
        <Comments />
      </Route>
    </Fragment>

);
};

export default QuoteDetail;

## Writing More Flexible Routing Code

import { Fragment } from "react";
import { Link, Route, useParams, useRouteMatch } from "react-router-dom";

import Comments from "../components/comments/Comments";
import HighlightedQuote from "../components/quotes/HighlightedQuote";

const DUMMY_QUOTES = [
{ id: "q1", author: "Max", text: "Learning React is fun!" },
{ id: "q2", author: "Chris", text: "Learning React is great!" },
];

const QuoteDetail = () => {
const match = useRouteMatch();
const params = useParams();

const quote = DUMMY_QUOTES.find((quote) => quote.id === params.quoteId);

if (!quote) {
return <p>No Quote Found!</p>;
}

return (
<Fragment>
<HighlightedQuote text={quote.text} author={quote.author} />

      <Route path={`/quotes/${params.quoteId}`} exact>
        <div className="centered">
          <Link className="btn--flat" to={`${match.url}/comments`}>
            Load Comments
          </Link>
        </div>
      </Route>

      <Route path={`${match.path}/comments`}>
        <Comments />
      </Route>
    </Fragment>

);
};

export default QuoteDetail;

##

import { Fragment } from "react";
import { useHistory, useLocation } from "react-router-dom";

import QuoteItem from "./QuoteItem";
import classes from "./QuoteList.module.css";

const sortQuotes = (quotes, ascending) => {
return quotes.sort((quoteA, quoteB) => {
if (ascending) {
return quoteA.id > quoteB.id ? 1 : -1;
} else {
return quoteA.id < quoteB.id ? 1 : -1;
}
});
};

const QuoteList = (props) => {
const history = useHistory();
const location = useLocation();

const queryParams = new URLSearchParams(location.search);

const isSortingAscending = queryParams.get("sort") === "asc";

const sortedQuotes = sortQuotes(props.quotes, isSortingAscending);

const changeSortingHandler = () => {
history.push({
pathname: location.pathname,
search: `?sort=${isSortingAscending ? "desc" : "asc"}`,
});
};

return (
<Fragment>

<div className={classes.sorting}>
<button onClick={changeSortingHandler}>
Sort {isSortingAscending ? "Descending" : "Ascending"}
</button>
</div>
<ul className={classes.list}>
{sortedQuotes.map((quote) => (
<QuoteItem
            key={quote.id}
            id={quote.id}
            author={quote.author}
            text={quote.text}
          />
))}
</ul>
</Fragment>
);
};

export default QuoteList;

## Sending and Getting Quote Data via Http

const FIREBASE_DOMAIN = "https://react-http-18691-default-rtdb.firebaseio.com";

export async function getAllQuotes() {
const response = await fetch(`${FIREBASE_DOMAIN}/quotes.json`);
const data = await response.json();

if (!response.ok) {
throw new Error(data.message || "Could not fetch quotes.");
}

const transformedQuotes = [];

for (const key in data) {
const quoteObj = {
id: key,
...data[key],
};

    transformedQuotes.push(quoteObj);

}

return transformedQuotes;
}

export async function getSingleQuote(quoteId) {
const response = await fetch(`${FIREBASE_DOMAIN}/quotes/${quoteId}.json`);
const data = await response.json();

if (!response.ok) {
throw new Error(data.message || "Could not fetch quote.");
}

const loadedQuote = {
id: quoteId,
...data,
};

return loadedQuote;
}

export async function addQuote(quoteData) {
const response = await fetch(`${FIREBASE_DOMAIN}/quotes.json`, {
method: "POST",
body: JSON.stringify(quoteData),
headers: {
"Content-Type": "application/json",
},
});
const data = await response.json();

if (!response.ok) {
throw new Error(data.message || "Could not create quote.");
}

return null;
}

export async function addComment(requestData) {
const response = await fetch(
`${FIREBASE_DOMAIN}/comments/${requestData.quoteId}.json`,
{
method: "POST",
body: JSON.stringify(requestData.commentData),
headers: {
"Content-Type": "application/json",
},
}
);
const data = await response.json();

if (!response.ok) {
throw new Error(data.message || "Could not add comment.");
}

return { commentId: data.name };
}

export async function getAllComments(quoteId) {
const response = await fetch(`${FIREBASE_DOMAIN}/comments/${quoteId}.json`);

const data = await response.json();

if (!response.ok) {
throw new Error(data.message || "Could not get comments.");
}

const transformedComments = [];

for (const key in data) {
const commentObj = {
id: key,
...data[key],
};

    transformedComments.push(commentObj);

}

return transformedComments;
}

##

import { useReducer, useCallback } from 'react';

function httpReducer(state, action) {
if (action.type === 'SEND') {
return {
data: null,
error: null,
status: 'pending',
};
}

if (action.type === 'SUCCESS') {
return {
data: action.responseData,
error: null,
status: 'completed',
};
}

if (action.type === 'ERROR') {
return {
data: null,
error: action.errorMessage,
status: 'completed',
};
}

return state;
}

function useHttp(requestFunction, startWithPending = false) {
const [httpState, dispatch] = useReducer(httpReducer, {
status: startWithPending ? 'pending' : null,
data: null,
error: null,
});

const sendRequest = useCallback(
async function (requestData) {
dispatch({ type: 'SEND' });
try {
const responseData = await requestFunction(requestData);
dispatch({ type: 'SUCCESS', responseData });
} catch (error) {
dispatch({
type: 'ERROR',
errorMessage: error.message || 'Something went wrong!',
});
}
},
[requestFunction]
);

return {
sendRequest,
...httpState,
};
}

export default useHttp;

##

import { Fragment, useEffect } from "react";
import { Link, Route, useParams, useRouteMatch } from "react-router-dom";

import Comments from "../components/comments/Comments";
import HighlightedQuote from "../components/quotes/HighlightedQuote";
import LoadingSpinner from "../components/UI/LoadingSpinner";

import useHttp from "../hooks/use-http";
import { getSingleQuote } from "../lib/api";

const QuoteDetail = () => {
const match = useRouteMatch();
const params = useParams();

const { quoteId } = params;

const {
sendRequest,
status,
data: loadedQuote,
error,
} = useHttp(getSingleQuote, true);

useEffect(() => {
sendRequest(quoteId);
}, [sendRequest, quoteId]);

// const quote = DUMMY_QUOTES.find((quote) => quote.id === params.quoteId);

if (status === "pending") {
return (

<div className="centered">
<LoadingSpinner />
</div>
);
}

if (error) {
return <p className="centered">{error}</p>;
}

if (!loadedQuote.text) {
return <p>No Quote Found!</p>;
}

return (
<Fragment>
<HighlightedQuote text={loadedQuote.text} author={loadedQuote.author} />

      <Route path={match.path} exact>
        <div className="centered">
          <Link className="btn--flat" to={`${match.url}/comments`}>
            Load Comments
          </Link>
        </div>
      </Route>

      <Route path={`${match.path}/comments`}>
        <Comments />
      </Route>
    </Fragment>

);
};

export default QuoteDetail;

## Adding the "Comments" Features

import { useRef, useEffect } from "react";

import useHttp from "../../hooks/use-http";
import { addComment } from "../../lib/api";
import LoadingSpinner from "../UI/LoadingSpinner";
import classes from "./NewCommentForm.module.css";

const NewCommentForm = (props) => {
const commentTextRef = useRef();

const { sendRequest, status, error } = useHttp(addComment);

const { onAddedComment } = props;

useEffect(() => {
if (status === "completed" && !error) {
onAddedComment();
}
}, [status, error, onAddedComment]);

const submitFormHandler = (event) => {
event.preventDefault();

    // optional: Could validate here

    const enteredText = commentTextRef.current.value;

    sendRequest({
      commentData: {
        text: enteredText,
      },
      quoteId: props.quoteId,
    });

};

return (

<form className={classes.form} onSubmit={submitFormHandler}>
{status === "pending" && (
<div className="centered">
<LoadingSpinner />
</div>
)}
<div className={classes.control} onSubmit={submitFormHandler}>
<label htmlFor="comment">Your Comment</label>
<textarea id="comment" rows="5" ref={commentTextRef}></textarea>
</div>
<div className={classes.actions}>
<button className="btn">Add Comment</button>
</div>
</form>
);
};

export default NewCommentForm;

##

import CommentItem from './CommentItem';
import classes from './CommentsList.module.css';

const CommentsList = (props) => {
return (

<ul className={classes.comments}>
{props.comments.map((comment) => (
<CommentItem key={comment.id} text={comment.text} />
))}
</ul>
);
};

export default CommentsList;

##

import { useState, useEffect, useCallback } from "react";
import { useParams } from "react-router";

import classes from "./Comments.module.css";
import NewCommentForm from "./NewCommentForm";
import CommentsList from "./CommentsList";
import useHttp from "../../hooks/use-http";
import { getAllComments } from "../../lib/api";
import LoadingSpinner from "../UI/LoadingSpinner";

const Comments = () => {
const [isAddingComment, setIsAddingComment] = useState(false);
const params = useParams();

const { quoteId } = params;

const { sendRequest, status, data: loadedComments } = useHttp(getAllComments);

useEffect(() => {
sendRequest(quoteId);
}, [quoteId, sendRequest]);

const startAddCommentHandler = () => {
setIsAddingComment(true);
};

const addedCommentHandler = useCallback(() => {
sendRequest(quoteId);
}, [sendRequest, quoteId]);

let comments;

if (status === "pending") {
comments = (

<div className="centered">
<LoadingSpinner />
</div>
);
}

if (status === "completed" && loadedComments && loadedComments.length > 0) {
comments = <CommentsList comments={loadedComments} />;
}

if (
status === "completed" &&
(!loadedComments || loadedComments.length === 0)
) {
comments = <p className="centered">No comments were added yet!</p>;
}

return (

<section className={classes.comments}>
<h2>User Comments</h2>
{!isAddingComment && (
<button className="btn" onClick={startAddCommentHandler}>
Add a Comment
</button>
)}
{isAddingComment && (
<NewCommentForm
          quoteId={quoteId}
          onAddedComment={addedCommentHandler}
        />
)}
{comments}
</section>
);
};

export default Comments;

## SECTION 21: Deploying React Apps

## Deployment Steps

## Adding Lazy Loading

import React, { Suspense } from "react";
import { Route, Switch, Redirect } from "react-router-dom";

// import AllQuotes from "./pages/AllQuotes";
// import QuoteDetail from "./pages/QuoteDetail";
// import NewQuote from "./pages/NewQuote";
// import NotFound from "./pages/NotFound";
import Layout from "./components/layout/Layout";
import LoadingSpinner from "./components/UI/LoadingSpinner";

const AllQuotes = React.lazy(() => import("./pages/AllQuotes"));
const QuoteDetail = React.lazy(() => import("./pages/QuoteDetail"));
const NewQuote = React.lazy(() => import("./pages/NewQuote"));
const NotFound = React.lazy(() => import("./pages/NotFound"));

function App() {
return (
<Layout>
<Suspense
fallback={

<div className="centered">
<LoadingSpinner />
</div>
} >
<Switch>
<Route path="/" exact>
<Redirect to="/quotes" />
</Route>
<Route path="/quotes" exact>
<AllQuotes />
</Route>
<Route path="/quotes/:quoteId">
<QuoteDetail />
</Route>
<Route path="/new-quote">
<NewQuote />
</Route>
<Route path="*">
<NotFound />
</Route>
</Switch>
</Suspense>
</Layout>
);
}

export default App;

## Building The Code For Production

npm run build

## Getting Started With Deployment (Uploading Files)

Use: sudo ... in terminal.

## SECTION 22: Adding Authentication To React Apps

## What, How & Why

Not all users and visitors to the website should be able to access all content.

- Pages Locked unless logged in

- Data endpoints locked for non-authenticated users (change New Password function should be authenticated).

2 step process:

- Get access/permission
- Send request to protected resource with credentials

A "yes alone is not enough to then access protected resources (API endpoints). Easy to fake.

The part with sending and checking the credentials but the response sent over by the server to the client must be more than just a "yes" or "no".

Server-side Sessions: once it grants you access the server stores a unique identifier for the client. This identifier is also sent back to the client. Both parties know this identifier... can't be faked because server will recognize made-up/faked ids.
Works great if front and back-end are tightly coupled and back-end is stateful.

Authentication Tokens: Back-end is stateless and flexible. Decoupled front and back-end situation. Common with single page apps.
Validates user and password and creates a permission token (long algorithmic string) with a private key. Only the server knows how to create that token with its private key. React can use this token to make protected requests. And token can be verified to be authentic.

## Starting Setup & First Steps

https://firebase.google.com/docs/reference/rest/auth

## Adding User Signup

Unlock Firebase authentication in the project. See docs.

import { useRef, useState } from "react";

import classes from "./AuthForm.module.css";

const AuthForm = () => {
const emailInputRef = useRef();
const passwordInputRef = useRef();

const [isLogin, setIsLogin] = useState(true);

const switchAuthModeHandler = () => {
setIsLogin((prevState) => !prevState);
};

const submitHandler = (event) => {
event.preventDefault();

    const enteredEmail = emailInputRef.current.value;
    const enteredPassword = passwordInputRef.current.value;

    // optional: Add validation

    if (isLogin) {
    } else {
      fetch(
        `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`,
        {
          method: "POST",
          body: JSON.stringify({
            email: enteredEmail,
            password: enteredPassword,
            returnSecureToken: true,
          }),
          headers: {
            "Content-Type": "application/json",
          },
        }
      ).then((res) => {
        if (res.ok) {
          // ...
        } else {
          res.json().then((data) => {
            // show an error modal
            console.log(data);
          });
        }
      });
    }

};

return (

<section className={classes.auth}>
<h1>{isLogin ? "Login" : "Sign Up"}</h1>
<form onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="email">Your Email</label>
<input type="email" id="email" required ref={emailInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="password">Your Password</label>
<input
            type="password"
            id="password"
            required
            ref={passwordInputRef}
          />
</div>
<div className={classes.actions}>
<button>{isLogin ? "Login" : "Create Account"}</button>
<button
            type="button"
            className={classes.toggle}
            onClick={switchAuthModeHandler}
          >
{isLogin ? "Create new account" : "Login with existing account"}
</button>
</div>
</form>
</section>
);
};

export default AuthForm;

## Showing Feedback To The User

import { useRef, useState } from "react";

import classes from "./AuthForm.module.css";

const AuthForm = () => {
const emailInputRef = useRef();
const passwordInputRef = useRef();

const [isLogin, setIsLogin] = useState(true);
const [isLoading, setIsLoading] = useState(false);

const switchAuthModeHandler = () => {
setIsLogin((prevState) => !prevState);
};

const submitHandler = (event) => {
event.preventDefault();

    const enteredEmail = emailInputRef.current.value;
    const enteredPassword = passwordInputRef.current.value;

    // optional: Add validation

    setIsLoading(true);

    if (isLogin) {

    } else {
      fetch(
        `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`,
        {
          method: "POST",
          body: JSON.stringify({
            email: enteredEmail,
            password: enteredPassword,
            returnSecureToken: true,
          }),
          headers: {
            "Content-Type": "application/json",
          },
        }
      ).then((res) => {
        setIsLoading(false);
        if (res.ok) {
          // ...
        } else {
          res.json().then((data) => {
            // show an error modal
            let errorMessage = "Authentication failed!";
            // if (data && data.error && data.error.message) {
            //   errorMessage = data.error.message;
            // }
            // Set some state and show some modal or
            alert(errorMessage);
          });
        }
      });
    }

};

return (

<section className={classes.auth}>
<h1>{isLogin ? "Login" : "Sign Up"}</h1>
<form onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="email">Your Email</label>
<input type="email" id="email" required ref={emailInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="password">Your Password</label>
<input
            type="password"
            id="password"
            required
            ref={passwordInputRef}
          />
</div>
<div className={classes.actions}>
{!isLoading && (
<button>{isLogin ? "Login" : "Create Account"}</button>
)}
{isLoading && <p>Sending request...</p>}
<button
            type="button"
            className={classes.toggle}
            onClick={switchAuthModeHandler}
          >
{isLogin ? "Create new account" : "Login with existing account"}
</button>
</div>
</form>
</section>
);
};

export default AuthForm;

## Adding User Login

import { useRef, useState } from "react";

import classes from "./AuthForm.module.css";

const AuthForm = () => {
const emailInputRef = useRef();
const passwordInputRef = useRef();

const [isLogin, setIsLogin] = useState(true);
const [isLoading, setIsLoading] = useState(false);

const switchAuthModeHandler = () => {
setIsLogin((prevState) => !prevState);
};

const submitHandler = (event) => {
event.preventDefault();

    const enteredEmail = emailInputRef.current.value;
    const enteredPassword = passwordInputRef.current.value;

    // optional: Add validation

    setIsLoading(true);

    let url;
    if (isLogin) {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    } else {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    }
    fetch(url, {
      method: "POST",
      body: JSON.stringify({
        email: enteredEmail,
        password: enteredPassword,
        returnSecureToken: true,
      }),
      headers: {
        "Content-Type": "application/json",
      },
    })
      .then((res) => {
        setIsLoading(false);
        if (res.ok) {
          return res.json();
        } else {
          return res.json().then((data) => {
            // show an error modal
            let errorMessage = "Authentication failed!";
            // if (data && data.error && data.error.message) {
            //   errorMessage = data.error.message;
            // }
            // Set some state and show some modal or
            throw new Error(errorMessage);
          });
        }
      })
      .then((data) => {
        console.log(data);
      })
      .catch((err) => alert(err.message));

};

return (

<section className={classes.auth}>
<h1>{isLogin ? "Login" : "Sign Up"}</h1>
<form onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="email">Your Email</label>
<input type="email" id="email" required ref={emailInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="password">Your Password</label>
<input
            type="password"
            id="password"
            required
            ref={passwordInputRef}
          />
</div>
<div className={classes.actions}>
{!isLoading && (
<button>{isLogin ? "Login" : "Create Account"}</button>
)}
{isLoading && <p>Sending request...</p>}
<button
            type="button"
            className={classes.toggle}
            onClick={switchAuthModeHandler}
          >
{isLogin ? "Create new account" : "Login with existing account"}
</button>
</div>
</form>
</section>
);
};

export default AuthForm;

## Managing The Auth State With Context

Matching App-wide state? Use Context or Redux

import React, { useState } from "react";

const AuthContext = React.createContext({
token: "",
isLoggedIn: false,
login: (token) => {},
logout: () => {},
});

export const AuthContextProvider = (props) => {
const [token, setToken] = useState(null);

const userIsLoggedIn = !!token;

const loginHandler = (token) => {
setToken(token);
};

const logoutHandler = () => {
setToken(null);
};

const contextValue = {
token: token,
isLoggedIn: userIsLoggedIn,
login: loginHandler,
logout: logoutHandler,
};

return (
<AuthContext.Provider value={contextValue}>
{props.children}
</AuthContext.Provider>
);
};

export default AuthContext;

##

import ReactDOM from "react-dom";
import { BrowserRouter } from "react-router-dom";

import "./index.css";
import App from "./App";
import { AuthContextProvider } from "./store/auth-context";

ReactDOM.render(
<AuthContextProvider>
<BrowserRouter>
<App />
</BrowserRouter>
</AuthContextProvider>,
document.getElementById("root")
);

##

import { useContext, useRef, useState } from "react";
import AuthContext from "../../store/auth-context";

import classes from "./AuthForm.module.css";

const AuthForm = () => {
const emailInputRef = useRef();
const passwordInputRef = useRef();

const authCtx = useContext(AuthContext);

const [isLogin, setIsLogin] = useState(true);
const [isLoading, setIsLoading] = useState(false);

const switchAuthModeHandler = () => {
setIsLogin((prevState) => !prevState);
};

const submitHandler = (event) => {
event.preventDefault();

    const enteredEmail = emailInputRef.current.value;
    const enteredPassword = passwordInputRef.current.value;

    // optional: Add validation

    setIsLoading(true);

    let url;
    if (isLogin) {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    } else {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    }
    fetch(url, {
      method: "POST",
      body: JSON.stringify({
        email: enteredEmail,
        password: enteredPassword,
        returnSecureToken: true,
      }),
      headers: {
        "Content-Type": "application/json",
      },
    })
      .then((res) => {
        setIsLoading(false);
        if (res.ok) {
          return res.json();
        } else {
          return res.json().then((data) => {
            // show an error modal
            let errorMessage = "Authentication failed!";
            // if (data && data.error && data.error.message) {
            //   errorMessage = data.error.message;
            // }
            // Set some state and show some modal or
            throw new Error(errorMessage);
          });
        }
      })
      .then((data) => {
        authCtx.login(data.idToken);
      })
      .catch((err) => alert(err.message));

};

return (

<section className={classes.auth}>
<h1>{isLogin ? "Login" : "Sign Up"}</h1>
<form onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="email">Your Email</label>
<input type="email" id="email" required ref={emailInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="password">Your Password</label>
<input
            type="password"
            id="password"
            required
            ref={passwordInputRef}
          />
</div>
<div className={classes.actions}>
{!isLoading && (
<button>{isLogin ? "Login" : "Create Account"}</button>
)}
{isLoading && <p>Sending request...</p>}
<button
            type="button"
            className={classes.toggle}
            onClick={switchAuthModeHandler}
          >
{isLogin ? "Create new account" : "Login with existing account"}
</button>
</div>
</form>
</section>
);
};

export default AuthForm;

##

import { useContext } from "react";
import { Link } from "react-router-dom";
import AuthContext from "../../store/auth-context";

import classes from "./MainNavigation.module.css";

const MainNavigation = () => {
const authCtx = useContext(AuthContext);

const isLoggedIn = authCtx.isLoggedIn;

return (

<header className={classes.header}>
<Link to="/">
<div className={classes.logo}>React Auth</div>
</Link>
<nav>
<ul>
{!isLoggedIn && (
<li>
<Link to="/auth">Login</Link>
</li>
)}
{isLoggedIn && (
<li>
<Link to="/profile">Profile</Link>
</li>
)}
{isLoggedIn && (
<li>
<button>Logout</button>
</li>
)}
</ul>
</nav>
</header>
);
};

export default MainNavigation;

## Using The Token For Requests To Protected Resources

import { useContext, useRef } from "react";
import AuthContext from "../../store/auth-context";
import classes from "./ProfileForm.module.css";

const ProfileForm = () => {
const authCtx = useContext(AuthContext);

const newPasswordInputRef = useRef();

const submitHandler = (event) => {
event.preventDefault();

    const enteredNewPassword = newPasswordInputRef.current.value;

    // add validation

    // send request
    fetch(
      `https://identitytoolkit.googleapis.com/v1/accounts:update?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`,
      {
        method: "POST",
        body: JSON.stringify({
          idToken: authCtx.token,
          password: enteredNewPassword,
          returnSecureToken: false,
        }),
        headers: {
          "Content-Type": "application/json",
        },
      }
    ).then((res) => {
      // assumtion: No errors and always succeeds!
    });

};

return (

<form className={classes.form} onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="new-password">New Password</label>
<input
          type="password"
          id="new-password"
          minLength="6"
          ref={newPasswordInputRef}
        />
</div>
<div className={classes.action}>
<button>Change Password</button>
</div>
</form>
);
};

export default ProfileForm;

## Redirecting The User

Using useHistory from react-router-dom.

import { useContext, useRef } from "react";
import { useHistory } from "react-router-dom";
import AuthContext from "../../store/auth-context";
import classes from "./ProfileForm.module.css";

const ProfileForm = () => {
const history = useHistory();
const authCtx = useContext(AuthContext);

const newPasswordInputRef = useRef();

const submitHandler = (event) => {
event.preventDefault();

    const enteredNewPassword = newPasswordInputRef.current.value;

    // add validation

    // send request
    fetch(
      `https://identitytoolkit.googleapis.com/v1/accounts:update?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`,
      {
        method: "POST",
        body: JSON.stringify({
          idToken: authCtx.token,
          password: enteredNewPassword,
          returnSecureToken: false,
        }),
        headers: {
          "Content-Type": "application/json",
        },
      }
    ).then((res) => {
      // assumtion: No errors and always succeeds!
      history.replace("/");
    });

};

return (

<form className={classes.form} onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="new-password">New Password</label>
<input
          type="password"
          id="new-password"
          minLength="6"
          ref={newPasswordInputRef}
        />
</div>
<div className={classes.action}>
<button>Change Password</button>
</div>
</form>
);
};

export default ProfileForm;

## Adding Logout

import { useContext } from "react";
import { Link, useHistory } from "react-router-dom";
import AuthContext from "../../store/auth-context";

import classes from "./MainNavigation.module.css";

const MainNavigation = () => {
const history = useHistory();
const authCtx = useContext(AuthContext);

const isLoggedIn = authCtx.isLoggedIn;

const logoutHandler = () => {
authCtx.logout();
// optional: redirect the user
};

return (

<header className={classes.header}>
<Link to="/">
<div className={classes.logo}>React Auth</div>
</Link>
<nav>
<ul>
{!isLoggedIn && (
<li>
<Link to="/auth">Login</Link>
</li>
)}
{isLoggedIn && (
<li>
<Link to="/profile">Profile</Link>
</li>
)}
{isLoggedIn && (
<li>
<button onClick={logoutHandler}>Logout</button>
</li>
)}
</ul>
</nav>
</header>
);
};

export default MainNavigation;

## Protecting Frontend Pages

Navigation Guards!

import { useContext } from "react";
import { Switch, Route, Redirect } from "react-router-dom";

import Layout from "./components/Layout/Layout";
import UserProfile from "./components/Profile/UserProfile";
import AuthPage from "./pages/AuthPage";
import HomePage from "./pages/HomePage";
import AuthContext from "./store/auth-context";

function App() {
const authCtx = useContext(AuthContext);

return (
<Layout>
<Switch>
<Route path="/" exact>
<HomePage />
</Route>
{!authCtx.isLoggedIn}
<Route path="/auth">
<AuthPage />
</Route>
<Route path="/profile">
{authCtx.isLoggedIn && <UserProfile />}
{!authCtx.isLoggedIn && <Redirect to="auth" />}
</Route>
<Route path="*">
<Redirect to="/" />
</Route>
</Switch>
</Layout>
);
}

export default App;

## Persisting The User Authentication Status

import React, { useState } from "react";

const AuthContext = React.createContext({
token: "",
isLoggedIn: false,
login: (token) => {},
logout: () => {},
});

export const AuthContextProvider = (props) => {
const initialToken = localStorage.getItem("token");
const [token, setToken] = useState(initialToken);

const userIsLoggedIn = !!token;

const loginHandler = (token) => {
setToken(token);
localStorage.setItem("token", token);
};

const logoutHandler = () => {
setToken(null);
localStorage.removeItem("token");
};

const contextValue = {
token: token,
isLoggedIn: userIsLoggedIn,
login: loginHandler,
logout: logoutHandler,
};

return (
<AuthContext.Provider value={contextValue}>
{props.children}
</AuthContext.Provider>
);
};

export default AuthContext;

## Adding Auto-Logout

import { useContext, useRef, useState } from "react";
import { useHistory } from "react-router-dom";

import AuthContext from "../../store/auth-context";
import classes from "./AuthForm.module.css";

const AuthForm = () => {
const history = useHistory();
const emailInputRef = useRef();
const passwordInputRef = useRef();

const authCtx = useContext(AuthContext);

const [isLogin, setIsLogin] = useState(true);
const [isLoading, setIsLoading] = useState(false);

const switchAuthModeHandler = () => {
setIsLogin((prevState) => !prevState);
};

const submitHandler = (event) => {
event.preventDefault();

    const enteredEmail = emailInputRef.current.value;
    const enteredPassword = passwordInputRef.current.value;

    // optional: Add validation

    setIsLoading(true);

    let url;
    if (isLogin) {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signInWithPassword?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    } else {
      url = `https://identitytoolkit.googleapis.com/v1/accounts:signUp?key=AIzaSyDrhDPxsHtwcbA4aZjvmqz1eylAoT0lfFs`;
    }
    fetch(url, {
      method: "POST",
      body: JSON.stringify({
        email: enteredEmail,
        password: enteredPassword,
        returnSecureToken: true,
      }),
      headers: {
        "Content-Type": "application/json",
      },
    })
      .then((res) => {
        setIsLoading(false);
        if (res.ok) {
          return res.json();
        } else {
          return res.json().then((data) => {
            // show an error modal
            let errorMessage = "Authentication failed!";
            // if (data && data.error && data.error.message) {
            //   errorMessage = data.error.message;
            // }
            // Set some state and show some modal or
            throw new Error(errorMessage);
          });
        }
      })
      .then((data) => {
        const expirationTime = new Date(new Date().getTime() + (+data.expiresIn * 1000))
        authCtx.login(data.idToken, expirationTime.toISOString());
        history.replace("/");
      })
      .catch((err) => alert(err.message));

};

return (

<section className={classes.auth}>
<h1>{isLogin ? "Login" : "Sign Up"}</h1>
<form onSubmit={submitHandler}>
<div className={classes.control}>
<label htmlFor="email">Your Email</label>
<input type="email" id="email" required ref={emailInputRef} />
</div>
<div className={classes.control}>
<label htmlFor="password">Your Password</label>
<input
            type="password"
            id="password"
            required
            ref={passwordInputRef}
          />
</div>
<div className={classes.actions}>
{!isLoading && (
<button>{isLogin ? "Login" : "Create Account"}</button>
)}
{isLoading && <p>Sending request...</p>}
<button
            type="button"
            className={classes.toggle}
            onClick={switchAuthModeHandler}
          >
{isLogin ? "Create new account" : "Login with existing account"}
</button>
</div>
</form>
</section>
);
};

export default AuthForm;

##

import React, { useState } from "react";

const AuthContext = React.createContext({
token: "",
isLoggedIn: false,
login: (token) => {},
logout: () => {},
});

const calculateRemainingTime = (expirationTime) => {
const currentTime = new Date().getTime();
const adjustedExpirationTime = Date(expirationTime).getTime();

const remainingDuration = adjustedExpirationTime - currentTime;

return remainingDuration;
};

export const AuthContextProvider = (props) => {
const initialToken = localStorage.getItem("token");
const [token, setToken] = useState(initialToken);

const userIsLoggedIn = !!token;

const logoutHandler = () => {
setToken(null);
localStorage.removeItem("token");
};

const loginHandler = (token, expirationTime) => {
setToken(token);
localStorage.setItem("token", token);

    const remainingTime = calculateRemainingTime(expirationTime);

    setTimeout(logoutHandler, remainingTime);

};

const contextValue = {
token: token,
isLoggedIn: userIsLoggedIn,
login: loginHandler,
logout: logoutHandler,
};

return (
<AuthContext.Provider value={contextValue}>
{props.children}
</AuthContext.Provider>
);
};

export default AuthContext;

## Finishing Steps

import React, { useState, useEffect, useCallback } from "react";

const AuthContext = React.createContext({
token: "",
isLoggedIn: false,
login: (token) => {},
logout: () => {},
});

const calculateRemainingTime = (expirationTime) => {
const currentTime = new Date().getTime();
const adjustedExpirationTime = new Date(expirationTime).getTime();

const remainingDuration = adjustedExpirationTime - currentTime;

return remainingDuration;
};

let logoutTimer;

const retrieveStoredToken = () => {
const storedToken = localStorage.getItem("token");
const storedExpirationDate = localStorage.getItem("expirationTime");

const remainingTime = calculateRemainingTime(storedExpirationDate);

if (remainingTime <= 60000) {
localStorage.removeItem("token");
localStorage.removeItem("expirationTime");
return null;
}

return {
token: storedToken,
duration: remainingTime,
};
};

export const AuthContextProvider = (props) => {
const tokenData = retrieveStoredToken();
let initialToken;

if (tokenData) {
initialToken = tokenData.token;
}

const [token, setToken] = useState(initialToken);

const userIsLoggedIn = !!token;

const logoutHandler = useCallback(() => {
setToken(null);
localStorage.removeItem("token");
localStorage.removeItem("expirationTime");

    if (logoutTimer) {
      clearTimeout(logoutTimer);
    }

}, []);

const loginHandler = (token, expirationTime) => {
setToken(token);
localStorage.setItem("token", token);
localStorage.setItem("expirationTime", expirationTime);

    const remainingTime = calculateRemainingTime(expirationTime);

    logoutTimer = setTimeout(logoutHandler, remainingTime);

};

useEffect(() => {
if (tokenData) {
console.log(tokenData.duration);
logoutTimer = setTimeout(logoutHandler, tokenData.duration);
}
}, [tokenData, logoutHandler]);

const contextValue = {
token: token,
isLoggedIn: userIsLoggedIn,
login: loginHandler,
logout: logoutHandler,
};

return (
<AuthContext.Provider value={contextValue}>
{props.children}
</AuthContext.Provider>
);
};

export default AuthContext;

## SECTION 23: A (Pretty Deep Dive) Introduction to Next.js

## What is NextJS?

A fullstack framework for ReactJS.
Helps us not have to reinvent the wheel when building production quality website.

## Key Feature 1: Built-in Server-side Rendering (Improved SEO!)

## Key Feature 2: Simplified Routing with File-Based Routing

## Key Feature 3: Build Fullstack Apps

## Creating a New Next.js Project & App

npx install create-next-app

## Analyzing the Created Project

## Adding First Pages

import '../styles/globals.css'

function MyApp({ Component, pageProps }) {
return <Component {...pageProps} />
}

export default MyApp;

##

// our-domain.com/

const HomePage = () => {
return <h1>The Home Page</h1>;
};

export default HomePage;

##

// our-domain.com/news

const NewsPage = () => {
return <h1>The News Page</h1>;
};

export default NewsPage;

## Adding Nested Paths & Pages (Nested Routes)

news/something-important.js

// our-domain.com/news/something-important

const DetailPage = () => {
return <h1>The Detail Page</h1>;
};

export default DetailPage;

## Creating Dynamic Pages (with Parameters)

news/[newsId].js

## Extracting Dynamic Parameter Values

import { useRouter } from "next/router";

// our-domain.com/news/something-important

const DetailPage = () => {
const router = useRouter();

// console.log(router.query.newsId);

const newsId = router.query.newsId;

// send a request to the backend API
// to fetch the news item with newsId

return <h1>The Detail Page</h1>;
};

export default DetailPage;

## Linking Between Pages

import Link from "next/link";
import { Fragment } from "react";

// our-domain.com/news

const NewsPage = () => {
return (
<Fragment>

<h1>The News Page</h1>
<ul>
<li>
<Link href="/news/nextjs-is-a-great-framework">
NextJS Is A Great Framework
</Link>
</li>
<li>Something Else</li>
</ul>
</Fragment>
);
};

export default NewsPage;

## Preparing the Project Pages

## Outputting a List of Meetups

import MeetupList from "../components/meetups/MeetupList";

const DUMMY_MEETUPS = [
{
id: "m1",
title: "A First Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
address: "Some address 5, 12345 Some City",
description: "This is a first meetup!",
},
{
id: "m2",
title: "A Second Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/f/f8/Schloss_Neuschwanstein_2013.jpg",
address: "Some address 10, 12345 Some City",
description: "This is a second meetup!",
},
];

const HomePage = () => {
return <MeetupList meetups={DUMMY_MEETUPS} />;
};

export default HomePage;

## Adding the New Meetup Form

import NewMeetupForm from "../../components/meetups/NewMeetupForm";

// our-domain.com/new-meetup

const addMeetupHandler = (enteredMeetupData) => {
console.log(enteredMeetupData);
};

const NewMeetupPage = () => {
return <NewMeetupForm onAddMeetup={addMeetupHandler} />;
};

export default NewMeetupPage;

## The "\_app.js" File & Layout Wrapper

import Layout from "../components/layout/Layout";
import "../styles/globals.css";

function MyApp({ Component, pageProps }) {
return (
<Layout>
{" "}
<Component {...pageProps} />
</Layout>
);
}

export default MyApp;

##

import MainNavigation from './MainNavigation';
import classes from './Layout.module.css';

function Layout(props) {
return (

<div>
<MainNavigation />
<main className={classes.main}>{props.children}</main>
</div>
);
}

export default Layout;

## Using Programmatic (Imperative) Navigation

import { useRouter } from "next/router";

import Card from "../ui/Card";
import classes from "./MeetupItem.module.css";

function MeetupItem(props) {
const router = useRouter();

const showDetailHandler = () => {
router.push("/" + props.id);
};
return (

<li className={classes.item}>
<Card>
<div className={classes.image}>
<img src={props.image} alt={props.title} />
</div>
<div className={classes.content}>
<h3>{props.title}</h3>
<address>{props.address}</address>
</div>
<div className={classes.actions}>
<button onClick={showDetailHandler}>Show Details</button>
</div>
</Card>
</li>
);
}

export default MeetupItem;

## Adding Custom Components & CSS Modules

import classes from "./MeetupDetail.module.css";

const MeetupDetail = (props) => {
return (

<section className={classes.detail}>
<img src={props.image} alt={props.title} />
<h1>{props.title}</h1>
<address>{props.address}</address>
<p>{props.description}</p>
</section>
);
};

export default MeetupDetail;

##

MeetupDetail.module.css

.detail {
text-align: center;
}

.detail img {
width: 100%;
}

## How Pre-rendering Works & Which Problem We Face

With useEffect running after the initial page render, the state array for loadedMeetups will be empty on this initial render... NextJS uses this first render to pre-render... the HTML of the DUMMY_MEETUPS won't be available and this is bad for SEO crawlers/scanners who would be looking for those crucial keywords in our data fetched.

import { useEffect, useState } from "react";
import MeetupList from "../components/meetups/MeetupList";

const DUMMY_MEETUPS = [
{
id: "m1",
title: "A First Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
address: "Some address 5, 12345 Some City",
description: "This is a first meetup!",
},
{
id: "m2",
title: "A Second Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/f/f8/Schloss_Neuschwanstein_2013.jpg",
address: "Some address 10, 12345 Some City",
description: "This is a second meetup!",
},
];

const HomePage = () => {
const [loadedMeetups, setLoadedMeetups] = useState([]);

useEffect(() => {
// send ttp request and fetch data
setLoadedMeetups(DUMMY_MEETUPS);
}, []);
return <MeetupList meetups={loadedMeetups} />;
};

export default HomePage;

## Data Fetching for Static Pages

getStaticProps is a reserved keyword and is executed during the npm run build process by NextJS... with this, the pre-render will have all it's html data from data fetch on initial render.

import MeetupList from "../components/meetups/MeetupList";

const DUMMY_MEETUPS = [
{
id: "m1",
title: "A First Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
address: "Some address 5, 12345 Some City",
description: "This is a first meetup!",
},
{
id: "m2",
title: "A Second Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/f/f8/Schloss_Neuschwanstein_2013.jpg",
address: "Some address 10, 12345 Some City",
description: "This is a second meetup!",
},
];

const HomePage = (props) => {
return <MeetupList meetups={props.meetups} />;
};

export const getStaticProps = async () => {
// fetch data from an API
return {
props: {
meetups: DUMMY_MEETUPS,
},
};
};

export default HomePage;

## More on Static Site Generation (SSG)

revalidate, in getStaticProps, triggers Next to create a new pre-rendering of the static pages every (n) seconds as long as the page is getting requests during that time

export const getStaticProps = async () => {
// fetch data from an API
return {
props: {
meetups: DUMMY_MEETUPS,
},
revalidate: 10,
};
};

## Exploring Server-side Rendering (SSR) with "getServerSideProps"

Guaranteed to work for every request to the server. So we'd have to wait for the page to be generated on every incoming request.

Good for data that changes multiple times per second.
Or if we need access to the complete request object...

import MeetupList from "../components/meetups/MeetupList";

const DUMMY_MEETUPS = [
{
id: "m1",
title: "A First Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
address: "Some address 5, 12345 Some City",
description: "This is a first meetup!",
},
{
id: "m2",
title: "A Second Meetup",
image:
"https://upload.wikimedia.org/wikipedia/commons/f/f8/Schloss_Neuschwanstein_2013.jpg",
address: "Some address 10, 12345 Some City",
description: "This is a second meetup!",
},
];

const HomePage = (props) => {
return <MeetupList meetups={props.meetups} />;
};

export const getServerSideProps = async (context) => {
const req = context.req;
const res = context.res;

// fetch data from an API

return {
props: {
meetups: DUMMY_MEETUPS,
},
};
};

// export const getStaticProps = async () => {
// // fetch data from an API
// return {
// props: {
// meetups: DUMMY_MEETUPS,
// },
// revalidate: 10,
// };
// };

export default HomePage;

## Working with Params for SSG Data Fetching

import MeetupDetail from "../../components/meetups/MeetupDetail";

const MeetupDetails = () => {
return (
<MeetupDetail
      image="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg"
      title="First Meetup"
      address="Some Street 5, Some City"
      description="This is a first meetup"
    />
);
};

export const getStaticProps = (context) => {
// fetch data for single meetup

const meetupId = context.params.meetupId;

return {
props: {
meetupData: {
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
id: meetupId,
title: "First Meetup",
address: "Some Street 5, Some City",
description: "This is a first meetup",
},
},
};
};

export default MeetupDetails;

## Preparing Paths with "getStaticPaths" & Working With Fallback Pages

import MeetupDetail from "../../components/meetups/MeetupDetail";

const MeetupDetails = () => {
return (
<MeetupDetail
      image="https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg"
      title="First Meetup"
      address="Some Street 5, Some City"
      description="This is a first meetup"
    />
);
};

export const getStaticPaths = async () => {
return {
fallback: false,
paths: [
{
params: {
meetupId: "m1",
},
},
{
params: {
meetupId: "m2",
},
},
],
};
};

export const getStaticProps = (context) => {
// fetch data for single meetup

const meetupId = context.params.meetupId;

return {
props: {
meetupData: {
image:
"https://upload.wikimedia.org/wikipedia/commons/thumb/d/d3/Stadtbild_M%C3%BCnchen.jpg/1280px-Stadtbild_M%C3%BCnchen.jpg",
id: meetupId,
title: "First Meetup",
address: "Some Street 5, Some City",
description: "This is a first meetup",
},
},
};
};

export default MeetupDetails;

## Introducing API Routes

Add api folder in pages folder.

JS files with names that'll serve as api routes.

Functions that contain server-side code. These functions are triggered whenever a request is sent to the route.

// /api/new-meetup
// POST /api/new-meetup

const handler = (req, res) => {
if (req.method === "POST") {
const data = req.body;

    const { title, image, address, description } = data;

    // store in database

}
};

export default handler;

## Working with MongoDB

import { MongoClient } from "mongodb";

// /api/new-meetup
// POST /api/new-meetup

const handler = async (req, res) => {
if (req.method === "POST") {
const data = req.body;

    // const { title, image, address, description } = data;

    // store in database
    const client = await MongoClient.connect(
      "mongodb+srv://cfrancis1989:Greenone?27!@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
    );

    const db = client.db();

    const meetupsCollection = db.collection("meetups");

    const result = await meetupsCollection.insertOne(data);

    console.log(result);

    client.close();

    res.status(201).json({ message: "Meetup inserted!" });

}
};

export default handler;

## Sending Http Requests To Our API Routes

import { useRouter } from "next/router";
import NewMeetupForm from "../../components/meetups/NewMeetupForm";

// our-domain.com/new-meetup

const NewMeetupPage = () => {
const router = useRouter();

const addMeetupHandler = async (enteredMeetupData) => {
const response = await fetch("/api/new-meetup", {
method: "POST",
body: JSON.stringify(enteredMeetupData),
headers: {
"Content-Type": "application/json",
},
});

    const data = await response.json();

    console.log(data);

    router.push("/");

};
return <NewMeetupForm onAddMeetup={addMeetupHandler} />;
};

export default NewMeetupPage;

## Getting Data From The Database

import { MongoClient } from "mongodb";

import MeetupList from "../components/meetups/MeetupList";

const HomePage = (props) => {
return <MeetupList meetups={props.meetups} />;
};

// export const getServerSideProps = async (context) => {
// const req = context.req;
// const res = context.res;

// // fetch data from an API

// return {
// props: {
// meetups: DUMMY_MEETUPS,
// },
// };
// };

export const getStaticProps = async () => {
// fetch data from an API
const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const meetups = await meetupsCollection.find().toArray();

client.close();

return {
props: {
meetups: meetups.map((meetup) => ({
title: meetup.title,
address: meetup.address,
image: meetup.image,
id: meetup.\_id.toString(),
})),
},
revalidate: 10,
};
};

export default HomePage;

## Getting Meetup Details Data & Preparing Pages

import { MongoClient } from "mongodb";

import MeetupList from "../components/meetups/MeetupList";

const HomePage = (props) => {
return <MeetupList meetups={props.meetups} />;
};

// export const getServerSideProps = async (context) => {
// const req = context.req;
// const res = context.res;

// // fetch data from an API

// return {
// props: {
// meetups: DUMMY_MEETUPS,
// },
// };
// };

export const getStaticProps = async () => {
// fetch data from an API
const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const meetups = await meetupsCollection.find().toArray();

client.close();

return {
props: {
meetups: meetups.map((meetup) => ({
title: meetup.title,
address: meetup.address,
image: meetup.image,
id: meetup.\_id.toString(),
})),
},
revalidate: 10,
};
};

export default HomePage;

##

import { MongoClient, ObjectId } from "mongodb";

import MeetupDetail from "../../components/meetups/MeetupDetail";

const MeetupDetails = (props) => {
return (
<MeetupDetail
      image={props.meetupData.image}
      title={props.meetupData.title}
      address={props.meetupData.address}
      description={props.meetupData.description}
    />
);
};

export const getStaticPaths = async () => {
// fetch data from an API
const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const meetups = await meetupsCollection.find({}, { \_id: 1 }).toArray();

client.close();

return {
fallback: false,
paths: meetups.map((meetup) => ({
params: {
meetupId: meetup.\_id.toString(),
},
})),
};
};

export const getStaticProps = async (context) => {
// fetch data for single meetup

const meetupId = context.params.meetupId;

const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const selectedMeetup = await meetupsCollection.findOne({
\_id: ObjectId(meetupId),
});

client.close();

return {
props: {
meetupData: {
id: selectedMeetup.\_id.toString(),
title: selectedMeetup.title,
address: selectedMeetup.address,
image: selectedMeetup.image,
description: selectedMeetup.description,
},
},
};
};

export default MeetupDetails;

## Adding "head" Metadata

import Head from "next/head";
import { Fragment } from "react";
import { MongoClient } from "mongodb";

import MeetupList from "../components/meetups/MeetupList";

const HomePage = (props) => {
return (
<Fragment>

<Head>
<title>React Meetups</title>
<meta
          name="description"
          content="Browse a Huge list of highly active React meetups!"
        />
</Head>
<MeetupList meetups={props.meetups} />
</Fragment>
);
};

// export const getServerSideProps = async (context) => {
// const req = context.req;
// const res = context.res;

// // fetch data from an API

// return {
// props: {
// meetups: DUMMY_MEETUPS,
// },
// };
// };

export const getStaticProps = async () => {
// fetch data from an API
const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const meetups = await meetupsCollection.find().toArray();

client.close();

return {
props: {
meetups: meetups.map((meetup) => ({
title: meetup.title,
address: meetup.address,
image: meetup.image,
id: meetup.\_id.toString(),
})),
},
revalidate: 10,
};
};

export default HomePage;

##

import { Fragment } from "react";
import Head from "next/head";
import { MongoClient, ObjectId } from "mongodb";

import MeetupDetail from "../../components/meetups/MeetupDetail";

const MeetupDetails = (props) => {
return (
<Fragment>

<Head>
<title>{props.meetupData.title}</title>
<meta name="description" content={props.meetupData.description} />
</Head>
<MeetupDetail
        image={props.meetupData.image}
        title={props.meetupData.title}
        address={props.meetupData.address}
        description={props.meetupData.description}
      />
</Fragment>
);
};

export const getStaticPaths = async () => {
// fetch data from an API
const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const meetups = await meetupsCollection.find({}, { \_id: 1 }).toArray();

client.close();

return {
fallback: false,
paths: meetups.map((meetup) => ({
params: {
meetupId: meetup.\_id.toString(),
},
})),
};
};

export const getStaticProps = async (context) => {
// fetch data for single meetup

const meetupId = context.params.meetupId;

const client = await MongoClient.connect(
"mongodb+srv://cfrancis1989:lFwzQY2XJsRukMzn@cluster0.aswpe.mongodb.net/meetups?retryWrites=true&w=majority"
);

const db = client.db();

const meetupsCollection = db.collection("meetups");

const selectedMeetup = await meetupsCollection.findOne({
\_id: ObjectId(meetupId),
});

client.close();

return {
props: {
meetupData: {
id: selectedMeetup.\_id.toString(),
title: selectedMeetup.title,
address: selectedMeetup.address,
image: selectedMeetup.image,
description: selectedMeetup.description,
},
},
};
};

export default MeetupDetails;

## Deploying Next.js Projects

## Using Fallback Pages & Re-deploying

##

##

##

##

##

##

##

##

##

##
