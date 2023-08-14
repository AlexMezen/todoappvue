# todoappvue

Vue3 ToDo App

## About project

```
This project is a ToDo application built using Vue 3, designed to help users manage their tasks efficiently. The app provides a user interface to create, edit, and remove ToDo items, and also allows marking them as done.
```

# Components

```
App.vue - The main component that orchestrates the entire application. It renders the header, ToDo creation button, ToDo creation dialog, and the list of ToDo items.

ToDoButton.vue - A simple button component used to trigger actions like opening the ToDo creation dialog.

ToDoInput.vue - A reusable input component used for capturing text input, both for ToDo titles and descriptions.

DialogToDo.vue - A dialog component that wraps other components and is used to display forms or content as a modal dialog. It emits events to show or hide itself.

ToDoForm.vue - A form component for creating new ToDo items. It contains inputs for ToDo title and description and a button to create a new ToDo.

ToDoList.vue - Displays the list of ToDo items. Uses transitions for smoother animations when items are added or removed.

ToDoItem.vue - Represents an individual ToDo item. It can display the title, description, and a checkmark indicating whether the task is done. It also has buttons to edit, delete, or mark the task as done.
```

## Functionality

```
Users can create new ToDo items by clicking the "Create todo" button. This triggers the display of a dialog containing the ToDo creation form.
The ToDo creation form captures both the title and description of the ToDo item. Once created, the form resets for new inputs.
The list of ToDo items is displayed below the creation button. If there are no items, a message indicating that the list is empty is displayed.
Each ToDo item is presented with its title, description, and buttons for editing, deleting, and marking as done.
ToDo items can be edited by clicking the "Edit" button. This replaces the display with input fields for modifying the title and description.
ToDo items can be marked as done by clicking the "Done" button. The status of being done is represented by a checkmark.
ToDo items can be deleted by clicking the "Delete" button.
The state of ToDo items (including creation, deletion, and editing) is persisted in the browser's local storage, ensuring that data is retained even after page refreshes.
```

## Getting Started

To get a local copy up and running follow these simple example steps.

### Prerequisites

- npm
  ```
  npm install npm@latest -g
  ```
- Node.js
  ```
  install Node.js on the official website
  ```


### Installation

How to run

1. Clone the repo
   ```
   git clone https://github.com/AlexMezen/todoappvue

2. Install NPM packages
   ```
   npm install
   ```
   ```
   npm run serve
   ```


### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
