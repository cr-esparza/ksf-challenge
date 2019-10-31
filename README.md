# ksf-app Code challenge
- The framework used to build this app is Vue.js.
[Vue](https://vuejs.org/)

- Vuetify is framework used to integrate google material design in a Vue app.
[Vuetify](https://vuetifyjs.com/)

- Axios is the library used to make the API calls, it works great with Vue
[Axios](https://github.com/axios/axios)

## Project setup
- To install the project run in the terminal.

```
npm install
```

### Compiles and hot-reloads for development
- To run the app in development mode with hot reload on every change run in terminal.

```
npm run serve
```

The app will executed in:
http://localhost:8080/

The project has 3 main views:
- Login: The user input the credentials to log in.
[login] (http://localhost:8080/)

- About: Assumptions, tradeoffs and things to improve in the project.
[about] (http://localhost:8080/about)

- Users: User profile data view. After log in the user will be redirected
to this view. Only the address is enabled to be edited, all the other fields are read only. This view is not accesible without a token (stored in localStorage)
[users] (http://localhost:8080/users/:id)


### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

#### Assumptions and tradeoffs 
- Form validations, at the moment no validation have been done. Most of the fields should be checked.
- To give feedback to the user when the update has been successful. At the moment if the update is successful only an alert is displayed.
- Improve error handling. The error handling needs to be improved for the whole aplication.
- Styling needs to be improved in the whole app. To work with graphic designer would be handy.
- User is not log out. At the moment the user is not able to log out.
- No conditional rendering implemented at the moment. If an user is logged in, then the log in view should not be visible, as well if the localStorage.token has no token, then the user shall not be able to see the users view.