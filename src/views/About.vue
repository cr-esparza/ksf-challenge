<template>
  <div class="about">
    <h1>Assumptions and things to improve</h1>
    <ul style="text-align: left;">
      <li>Form validations, at the moment no validation have been done. Most of the fields should be checked.</li>
      <li>To give feedback to the user when the update has been successful. At the moment if the update is successful only an alert is displayed.</li>
      <li>Improve error handling. The error handling needs to be improved for the whole aplication.</li>
      <li>Styling needs to be improved in the whole app. To work with graphic designer would be handy.</li>
      <li>User is not log out. At the moment the user is not able to log out.</li>
      <li>No conditional rendering implemented at the moment. If an user is logged in, then the log in view should not be visible, as well if the localStorage.token has no token, then the user shall not be able to see the users view.</li>
    </ul>
  </div>
</template>
