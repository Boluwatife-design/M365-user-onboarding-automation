# Create a sharepoint list with: 
  - First Name
  - Last Name
  - Department
  - Job Role
  - Manager
  - Start Date

# When an Item is created:
  - Put in the Site Address
  - Put in the list name

# Get Item: 
  - Put in the site address
  - Put it in the list name
  - Select ID (Dynamic) from sharepoint
  - Ensure you get all fields like:First Name, Last Name, Department, Role

# Compose:
  - Select expression :

        toLower(
          replace(
          concat(
            if(empty(outputs('Get_item')?['body/FirstName']), 'u', substring(outputs('Get_item')?['body/FirstName'], 0, 1)),
            '.',
            coalesce(outputs('Get_item')?['body/LastName'], 'user'),
            '@linkorgnet.com'
        ),
        ' ',
        ''
          )
        )

# Create user under entra:
  - Account Enabled - Yes
  - Display name (select expression)

        concat(coalesce(outputs('Get_item')?['body/LastName'], 'New'), ' ', coalesce(outputs('Get_item')?['body/LastName0'], 'User'))
  
  - Mail Nickname (select expression)
    
        toLower(replace(concat(if(empty(trim(string(outputs('Get_item')?['body/LastName']))), 'u', substring(trim(string(outputs('Get_item')?['body/LastName'])), 0, 1)), '.', if(empty(trim(string(outputs('Get_item')?['body/LastName0']))), 'user', trim(string(outputs('Get_item')?['body/LastName0'])))), ' ', ''))

# Password - Dynamic (your choice)
  - UPN (Select expression)

        toLower(replace(concat(if(empty(trim(string(outputs('Get_item')?['body/LastName']))), 'u', substring(trim(string(outputs('Get_item')?['body/LastName'])), 0, 1)), '.', if(empty(trim(string(outputs('Get_item')?['body/LastName0']))), 'user', trim(string(outputs('Get_item')?['body/LastName0']))), '@linkorgnet.com'), ' ', ''))






Add user to group (Entra) (this should be a security or dynamic group to automatically assign license )
User ID - Dynamic (ID)
Group ID - { object ID of group)
