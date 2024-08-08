# Requirements
The following requirements are coming from README.md file for the JWA Foundation Project for referencing purposes

## Software Requirements 
- Users should have unique usernames
- Usernames and passwords should not be longer than 30 characters
- Planet and Moon names should not have more than 30 characters
- Planets and moons should have unique names
- Planets should be “owned” by the user that added it to the Planetarium
- Moons should be “owned” by the Planet the User adding the moon associated it with
- Planets and Moons should allow adding an associated image, but an image should not be required for the data to be added to the database

## Use Cases
- Users should be able to open a new User account with the Planetarium
- Users should be able to securely access their account
- Users should be able to see planets and moons added to the Planetarium
- Users should be able to add new Planets to the Planetarium
- Users should be able to remove Planets from the Planetarium
- Users should be able to add Moons to the Planetarium associated with a Planet
- Users should be able to remove Moons from the Planetarium

## Testing Requirements
- All Test Reporting should be done in Jira
- All Use Cases require a minimum of one positive test
- All Use Cases with associated software requirements require negative testing to verify requirements are met
- All Use Cases with Software Requirements that limit data input require Boundary Analysis Testing
- All Use Cases with Software Requirements that limit data visibility require Error Guess Testing
- All Use Cases with Software Requirements that limit data interaction require Error Guess Testing
- All tests that fail should be logged in a Defect Report inside of Jira
- Acceptance testing for the user experience should answer the following questions in detail:
    - Is the intended use of the service intuitive?
    - Is the service easy to use?
    - Does the service inspire confidence?
    - Is the service pleasing to look at?

## Defect Report Requirements

- All Defect Reports should include the following information
    - unique id
    - description
    - associated Test Object
    - associated Test Data

# Use Case
These are my examples for Use Cases:
- Id: 1
- Name: User Registration
- Description: Users should be allow to register an account with the planetarium
- System: Planetarium Application
- Preconditions:
    - There does not exist new registered user with username:
        - "Batman and Robin Unite Now!!!!"
    - There exists registered user username:
        - "Batman"
- Actors:
    - User: 
        - creating a new account
    - Planetarium Application:
        - Handles account creation

- Id: 2
- Name: User Login
- Description: Users should be allow to securely login into an account with the planetarium
- System: Planetarium Application
- Preconditions:
    - There exists registered user username:
        - "Batman"
- Actors:
    - User: 
        - Login into an account
    - Planetarium Application:
        - Handles account login

- Id: 3
- Name: Planet Addition
- Description: Users should be allowed to add a planet with the planetarium
- System: Planetarium Application
- Preconditions:
    - There exist registered Planets with name:
        - "Earth"
        - "Mars"
    - There does not exists new registered Planet name:
        - "Jupiter"
- Actors:
    - User:
        - Adds new planet
    - Planetarium Application:
        - Handles planet addition

- Id: 4
- Name: Planet Deletion
- Description: Users should be allowed to delete a planet with the planetarium
- System: Planetarium Application
- Preconditions:
    - There exist registered Planets with name:
        - "Earth"
        - "Mars"
- Actors:
    - User:
        - select planet to delete
    - Planetarium Application:
        - Handles planet deletion


- Id: 5
- Name: Moon Addition
- Description: Users should be allowed to add a moon with the planetarium
- System: Planetarium Application
- Preconditions:
    - There exist registered Moons with name:
        - "Luna"
        - "Titan"
    - There does not exists new registered Planet name:
        - "Noom"
- Actors:
    - User:
        - Adds new moon
        - Selects associating planet for moon
    - Planetarium Application:
        - Handles moon addition

- Id: 6
- Name: Moon Deletion
- Description: Users should be allowed to delete a moon with the planetarium
- System: Planetarium Application
- Preconditions:
    - There exist registered Moons with name:
        - "Luna"
        - "Titan"
- Actors:
    - User:
        - select moon to delete
    - Planetarium Application:
        - Handles moon deletion

## Case Scenarios - User Registration
**Positive Use Case Data:**
- valid username = "Batman and Robin Unite Now!!!!"
- valid password = "Riddler and Joker Disagree!!!!"

**Negative Use Case Data:**
- non unique username = "Batman"
- too long username = "Gordon and Clark are friends!!!"
- too long password = "Reverse Flash strikes again!!!!"

**Positive Case Scenarios for Registration** 

Positive Case Scenario:
1. get to landing page
2. pick option to register
3. provide valid username
4. provide valid password
5. user should be registered with the planetarium application

**Negative Case Scenarios for Registration**

Negative Use Case Scenario Username Not Unique:
1. get to landing page
2. pick option to register
3. provide non-unique username
4. provide valid password
5. user should be informed the username is already taken

Negative Use Case Scenario Username Too Long:
1. get to landing page
2. pick option to register
3. provide too long username
4. provide valid password
5. user should be informed the username is too long

Negative Use Case Scenario Password Too Long:
1. get to landing page
2. pick option to register
3. provide valid username
4. provide too long password
5. user should be informed the password is too long

Negative Use Case Scenario Username Not Unique and Password Too Long:
1. get to landing page
2. pick option to register
3. provide non-unique username
4. provide too long password
5. user should be informed registration failed

Negative Use Case Scenario Credentials Too Long:
1. get to landing page
2. pick option to register
3. provide too long username
4. provide too long password
5. user should be informed the username and password are too long

**Decision Table - Registration:**

<table>
    <tr>
        <th>Scenario</th><th>Username</th><th>Password</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Use Case Scenario:</td><td>valid username</td><td>valid password</td><td>user registered</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Username Not Unique:</td><td>non-unique username</td><td>valid password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Username Too Long:</td><td>too long username</td><td>valid password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Password Too Long:</td><td>valid username</td><td>too long password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Username Not Unique and Password Too Long:</td><td>non-unique username</td><td>too long password</td><td>user not registered</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Credentials Too Long:</td><td>too long username</td><td>too long password</td><td>user not registered</td>
    </tr>
</table>

## Case Scenarios - User Login
**Positive Use Case Data:**
- if testing before registration test
    - valid username1 = "Batman"
    - valid password1 = "I am the night"
- if testing after registration test (verifies registration step works as intended)
    - valid username2 = "Batman and Robin Unite Now!!!!" 
    - valid password2 = "Riddler and Joker Disagree!!!!"

**Negative Use Case Data:**
- testing matching username or password
    - wrong username = "Batman!"
    - wrong password = "I am the day"
- testing bug incorrect passing (verifies registration constraint works as intended)
    - invalid username = "Gordon and Clark are friends!!!"
    - invalid password = "Reverse Flash strikes again!!!!"

**Positive Case Scenarios for Login** 

Positive Case Scenario with Pre-Registered Data:
1. get to landing page
2. provide valid username
3. provide valid password
4. click login button
5. user should be logged in into the planetarium application

Positive Case Scenario with Post-Registered Data:
1. get to landing page
2. provide valid username
3. provide valid password
4. click login button
5. user should be logged in into the planetarium application

**Negative Case Scenarios for Login**

Negative Use Case Scenario Wrong Username:
1. get to landing page
2. provide wrong username
3. provide valid password
4. click login button
5. user should be informed that one or both credentials are incorrect

Negative Use Case Scenario Wrong Password:
1. get to landing page
2. provide valid username
3. provide wrong password
4. click login button
5. user should be informed that one or both credentials are incorrect

Negative Use Case Scenario Wrong Credentials:
1. get to landing page
2. provide wrong username
3. provide wrong password
4. click login button
5. user should be informed that one or both credentials are incorrect

Negative Use Case Scenario Invalid Username:
1. get to landing page 
2. provide invalid username
3. provide valid password
4. click login button
5. user should be informed that one or both credentials are incorrect

Negative Use Case Scenario Invalid password:
1. get to landing page
2. provide valid username
3. provide invalid password
4. click login button
5. user should be informed that one or both credentials are incorrect

Negative Use Case Scenario Invalid Credentials:
1. get to landing page
2. provide invalid username
3. provide invalid password
4. click login button
5. user should be informed that one or both credentials are incorrect

**Decision Table - login:**

<table>
    <tr>
        <th>Scenario</th><th>Username</th><th>Password</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Case Scenario with Pre-Registered Data:</td><td>valid username1</td><td>valid password1</td><td>user logged in</td>
    </tr>
        <tr>
        <td>Positive Case Scenario with Post-Registered Data:</td><td>valid username2</td><td>valid password2</td><td>user logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Wrong Username:</td><td>wrong username</td><td>valid password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Wrong Password:</td><td>valid username</td><td>wrong password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Wrong Credentials:</td><td>wrong username</td><td>wrong password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Invalid Username:</td><td>invalid username</td><td>valid password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Invalid Password:</td><td>valid username</td><td>invalid password</td><td>user not logged in</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Invalid Credentials:</td><td>invalid username</td><td>invalid password</td><td>user not logged in</td>
    </tr>
</table>

## Case Scenarios - Planet Addition

**Positive Use Case Data:**
- valid name = "I am the planet named Mars!!!!"
- valid image
- no image

**Negative Use Case Data:**
- non unique name = "Earth"
- too long name = "I am the existence of all being"
- invalid image
- moon name = "Luna"

**Positive Case Scenarios for Planet Addition** 

Positive Case Scenario With Image Data:
1. get to planetarium display page
2. provide valid name
3. click button to add image
4. provide valid image
5. click button to add planet
6. new planet should be added and displayed in Planetarium Application

Positive Case Scenario Without Image Data:
1. get to planetarium display page
2. provide valid name
3. do not provide image
4. click button to add planet
5. new planet should be added in Planetarium Application without image data

**Negative Case Scenarios for Planet Addition**

Negative Use Case Scenario Non Unique Name With Valid Image:
1. get to planetarium display page
2. provide non unique name
3. click button to add image
4. provide valid image
5. click button to add planet
6. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name With Valid Image:
1. get to planetarium display page
2. provide too long name
3. click button to add image
4. provide valid image
5. click button to add planet
6. user should be informed that the name is too long

Negative Use Case Scenario Non Unique Name Without Image:
1. get to planetarium display page
2. provide non unique name
3. do not provide image
4. click button to add planet
5. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name Without Image:
1. get to planetarium display page
2. provide too long name
3. do not provide image
4. click button to add planet
5. user should be informed that the name is too long

Negative Use Case Scenario Unique Name With Invalid Image:
1. get to planetarium display page
2. provide valid name
3. click button to add image
4. provide invalid image
5. click button to add planet
6. user should be informed that the image is invalid

Negative Use Case Scenario Non Unique Name With Invalid Image:
1. get to planetarium display page
2. provide non unique name
3. click button to add image
4. provide invalid image
5. click button to add planet
6. user should be informed that the name is taken or image is invalid

Negative Use Case Scenario Too Long Name With Invalid Image:
1. get to planetarium display page
2. provide too long name
3. click button to add image
4. provide invalid image
5. click button to add planet
6. user should be informed that the name is too long or image is invalid

Negative Use Case Scenario Moon Name With Valid Image:
1. get to planetarium display page
2. provide moon name
3. click button to add image
4. provide valid image
5. click button to add planet
6. user should be informed that the name belongs to a moon

Negative Use Case Scenario Moon Name With Invalid Image:
1. get to planetarium display page
2. provide moon name
3. click button to add image
4. provide invalid image
5. click button to add planet
6. user should be informed that the name belongs to a moon or image is invalid

Negative Use Case Scenario Moon Name With No Image:
1. get to planetarium display page
2. provide moon name
3. do not provide image
4. click button to add planet
5. user should be informed that the name belongs to a moon

**Decision Table - Planet Addition:**

<table>
    <tr>
        <th>Scenario</th><th>Planet Name</th><th>Image</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Case Scenario With Image Data:</td><td>valid name</td><td>valid image</td><td>planet added</td>
    </tr>
        <tr>
        <td>Positive Case Scenario Without Image Data:</td><td>valid name</td><td>no image</td><td>planet added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name With Valid Image:</td><td>non unique name</td><td>valid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name With Valid Image:</td><td>too long name</td><td>valid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name Without Image:</td><td>non unique name</td><td>no image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name Without Image:</td><td>too long name</td><td>no image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Unique Name With Invalid Image:</td><td>valid name</td><td>invalid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name With Invalid Image:</td><td>non unique name</td><td>invalid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name With Invalid Image:</td><td>too long name</td><td>invalid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Moon Name With Valid Image:</td><td>moon name</td><td>valid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Moon Name With Invalid Image:</td><td>moon name</td><td>invalid image</td><td>planet not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Moon Name Without Image:</td><td>moon name</td><td>no image</td><td>planet not added</td>
    </tr>
</table>

## Case Scenarios - Planet Deletion

**Positive Use Case Data:**
- valid pre existing name = "Earth"
- valid existing name = "I am the planet named Mars!!!!"

**Negative Use Case Data:**
- invalid name = "Earths"
- invalid deleted name = "Earth"
- invalid too long name = "I am the existence of all being"
- moon name = "Luna"

**Positive Case Scenarios for Planet Deletion** 

Positive Case Scenario With Pre-Existing Name:
1. get to planetarium display page
2. provide pre exisiting valid name
3. click button to delete planet
4. planet should be deleted and undisplayed from Planetarium Application

Positive Case Scenario With Existing Name:
1. get to planetarium display page
2. provide exisiting valid name
3. click button to delete planet
4. planet should be deleted and undisplayed from Planetarium Application

**Negative Case Scenarios for Planet Deletion**

Negative Use Case Scenario Invalid Name:
1. get to planetarium display page
2. provide invalid name
3. click button to delete planet
4. Planetarium Application should alert that the planet does not exist to delete

Negative Use Case Scenario Deleted Name:
1. get to planetarium display page
2. provide invalid deleted name
3. click button to delete planet
4. Planetarium Application should alert that the planet does not exist to delete

Negative Use Case Scenario Too Long Name:
1. get to planetarium display page
2. provide invalid too long name
3. click button to delete planet
4. Planetarium Application should alert that the name is too long or does not exist to delete

Negative Use Case Scenario Moon Name:
1. get to planetarium display page
2. provide moon name
3. click button to delete planet
4. Planetarium Application should alert that the name belongs to a moon and must delete planet

**Decision Table - Planet Deletion:**

<table>
    <tr>
        <th>Scenario</th><th>Planet Name</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Case Scenario With Pre-Existing Name:</td><td>pre existing name</td><td>planet deleted</td>
    </tr>
    <tr>
        <td>Positive Case Scenario With Existing Name:</td><td>existing name</td><td>planet deleted</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Invalid Name:</td><td>invalid name</td><td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Deleted Name:</td><td>deleted name</td><td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name:</td><td>too long name</td><<td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Moon Name:</td><td>moon name</td><<td>no deletion</td>
    </tr>
</table>

## Case Scenarios - Moon Addition

**Positive Use Case Data:**
- valid name = "I am the moon named Noom!!!!!!"
- valid image
- no image

**Negative Use Case Data:**
- non unique name = "Luna"
- too long name = "I am the existence of all moons"
- invalid image
- planet name = "Mars"

**Positive Case Scenarios for Moon Addition** 

Positive Case Scenario With Image Data:
1. get to planetarium display page
2. provide valid name
3. provide valid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. new moon should be added and displayed in Planetarium Application

Positive Case Scenario Without Image Data:
1. get to planetarium display page
2. provide valid name
3. provide valid planet id
4. do not provide image
5. click button to add moon
6. new moon should be added in Planetarium Application without image data

**Negative Case Scenarios for Moon Addition**

Negative Use Case Scenario Non Unique Name With Valid Image:
1. get to planetarium display page
2. provide non unique name
3. provide valid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name With Valid Image:
1. get to planetarium display page
2. provide too long name
3. provide valid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name is too long

Negative Use Case Scenario Non Unique Name Without Image:
1. get to planetarium display page
2. provide non unique name
3. provide valid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name Without Image:
1. get to planetarium display page
2. provide too long name
3. provide valid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name is too long

Negative Use Case Scenario Unique Name With Invalid Image:
1. get to planetarium display page
2. provide valid name
3. provide valid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the image is invalid

Negative Use Case Scenario Non Unique Name With Invalid Image:
1. get to planetarium display page
2. provide non unique name
3. provide valid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name is taken or image is invalid

Negative Use Case Scenario Too Long Name With Invalid Image:
1. get to planetarium display page
2. provide too long name
3. provide valid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name is too long or image is invalid

Negative Use Case Scenario Planet Name With Valid Image:
1. get to planetarium display page
2. provide planet name
3. provide valid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name belongs to a planet

Negative Use Case Scenario Planet Name With Invalid Image:
1. get to planetarium display page
2. provide planet name
3. provide valid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name belongs to a planet or image is invalid

Negative Use Case Scenario Planet Name With No Image:
1. get to planetarium display page
2. provide planet name
3. provide valid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name belongs to a planet

Negative Use Case Scenario Non Unique Name With Valid Image Invalid ID:
1. get to planetarium display page
2. provide non unique name
3. provide invalid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name With Valid Image Invalid ID:
1. get to planetarium display page
2. provide too long name
3. provide invalid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name is too long

Negative Use Case Scenario Non Unique Name Without Image Invalid ID:
1. get to planetarium display page
2. provide non unique name
3. provide invalid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name is taken

Negative Use Case Scenario Too Long Name Without Image Invalid ID:
1. get to planetarium display page
2. provide too long name
3. provide invalid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name is too long

Negative Use Case Scenario Unique Name With Invalid Image Invalid ID:
1. get to planetarium display page
2. provide valid name
3. provide invalid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the image is invalid

Negative Use Case Scenario Non Unique Name With Invalid Image Invalid ID:
1. get to planetarium display page
2. provide non unique name
3. provide invalid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name is taken or image is invalid

Negative Use Case Scenario Too Long Name With Invalid Image Invalid ID:
1. get to planetarium display page
2. provide too long name
3. provide invalid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name is too long or image is invalid

Negative Use Case Scenario Planet Name With Valid Image Invalid ID:
1. get to planetarium display page
2. provide planet name
3. provide invalid planet id
4. click button to add image
5. provide valid image
6. click button to add moon
7. user should be informed that the name belongs to a planet

Negative Use Case Scenario Planet Name With Invalid Image Invalid ID:
1. get to planetarium display page
2. provide planet name
3. provide invalid planet id
4. click button to add image
5. provide invalid image
6. click button to add moon
7. user should be informed that the name belongs to a planet or image is invalid

Negative Use Case Scenario Planet Name With No Image Invalid ID:
1. get to planetarium display page
2. provide planet name
3. provide invalid planet id
4. do not provide image
5. click button to add moon
6. user should be informed that the name belongs to a planet

**Decision Table - Moon Addition:**

<table>
    <tr>
        <th>Scenario</th><th>Moon Name</th><th>Image</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Case Scenario with Image Data:</td><td>valid name</td><td>valid image</td><td>moon added</td>
    </tr>
        <tr>
        <td>Positive Case Scenario Without Image Data:</td><td>valid name</td><td>no image</td><td>moon added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name With Valid Image:</td><td>non unique name</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name With Valid Image:</td><td>too long name</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name Without Image:</td><td>non unique name</td><td>no image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name Without Image:</td><td>too long name</td><td>no image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Unique Name With Invalid Image:</td><td>valid name</td><td>invalid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Non Unique Name With Invalid Image:</td><td>non unique name</td><td>invalid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name With Invalid Image:</td><td>too long name</td><td>invalid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Planet Name With Valid Image:</td><td>planet name</td><td>valid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Planet Name With Invalid Image:</td><td>planet name</td><td>invalid image</td><td>moon not added</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Planet Name Without Image:</td><td>planet name</td><td>no image</td><td>moon not added</td>
    </tr>
</table>

## Case Scenarios - Moon Deletion

**Positive Use Case Data:**
- valid pre existing name = "Luna"
- valid existing name = "I am the moon named Noom!!!!!!"

**Negative Use Case Data:**
- invalid name = "Lunas"
- invalid deleted name = "Luna"
- invalid too long name = "I am the existence of all moons"
- planet name = "Mars"

**Positive Case Scenarios for Moon Deletion** 

Positive Case Scenario With Pre-Existing Name:
1. get to planetarium display page
2. provide pre exisiting valid name
3. click button to delete moon
4. moon should be deleted and undisplayed from Planetarium Application

Positive Case Scenario With Existing Name:
1. get to planetarium display page
2. provide exisiting valid name
3. click button to delete moon
4. moon should be deleted and undisplayed from Planetarium Application

**Negative Case Scenarios for Planet Deletion**

Negative Use Case Scenario Invalid Name:
1. get to planetarium display page
2. provide invalid name
3. click button to delete moon
4. Planetarium Application should alert that the moon does not exist to delete

Negative Use Case Scenario Deleted Name:
1. get to planetarium display page
2. provide invalid deleted name
3. click button to delete moon
4. Planetarium Application should alert that the moon does not exist to delete

Negative Use Case Scenario Too Long Name:
1. get to planetarium display page
2. provide invalid too long name
3. click button to delete moon
4. Planetarium Application should alert that the name is too long or does not exist to delete

Negative Use Case Scenario Planet Name:
1. get to planetarium display page
2. provide planet name
3. click button to delete moon
4. Planetarium Application should alert that the name belongs to a planet and must delete moon

**Decision Table - Moon Deletion:**

<table>
    <tr>
        <th>Scenario</th><th>Moon Name</th><th>Expected Result</th>
    </tr>
    <tr>
        <td>Positive Case Scenario With Pre-Existing Name:</td><td>pre existing name</td><td>moon deleted</td>
    </tr>
    <tr>
        <td>Positive Case Scenario With Existing Name:</td><td>existing name</td><td>moon deleted</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Invalid Name:</td><td>invalid name</td><td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Deleted Name:</td><td>deleted name</td><td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Too Long Name:</td><td>too long name</td><<td>no deletion</td>
    </tr>
    <tr>
        <td>Negative Use Case Scenario Planet Name:</td><td>planet name</td><<td>no deletion</td>
    </tr>
</table>


Riddler and Jopker Disagre!!!!