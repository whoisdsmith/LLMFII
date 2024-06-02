---
aliases:
  - google-contacts-to-obsidian
tags:
  - "#python"
  - "#api"
  - "#software-development"
  - "#open-source"
  - "#data-visualization"

  - "#google-contacts"
  - "#obsidian"
  - "#graph-visualization"
---
# Google Contacts to Obsidian Graph

This Python script enables the download of Google contacts using the Google People API and converts each contact into a .md file format. This is particularly useful for visualizing your connections in tools like Obsidian, where you can create graphs displaying relationships between people. Alongside the script, a .md template is included that you can customize to suit your needs.

## Usage

1. Obtain an API key from the Google API console
2. Install the required Python libraries
3. Run the script to download contacts in .md format
4. Open the generated vault with Obsidian

### 1. API Key (Google Client Setup)
The first step to using the script is getting set up with Google credentials that the application case use.

- [Create Google Cloud Project](https://console.cloud.google.com/projectcreate?)
- [Activate Google People API](https://console.cloud.google.com/apis/api/people.googleapis.com)
- [Configure OAUTH Screen](https://console.cloud.google.com/apis/credentials/consent?)
  - Applcation should be **external**
  - Define scopes
    - .../auth/userinfo.profile
    - .../auth/contacts.readonly
    - .../auth/contacts.other.readonly
    - .../auth/directory.readonly
- Add Test users as needed
- Go to the [Credentials screen](https://console.cloud.google.com/apis/credentials) of the project and create a OAuth Client ID using the Create Credentials dropdown. Choose Desktop App as type
- Under 'Client seecrets' click on the **Download JSON** button, rename the file to '**credentials.json**' and place it in the same folder with the script 
  

### 2. Required Libraries
All required libraries for this script are listed in **requirements.txt** file.

### 3. Running the script
When you run the script, it will open your browser to complete OAuth2 authentication, accept everything, and once you've logged in, the download process will begin.

**Note**: Download limit is 2000 contacts!

### 4. Obsidian vault
After the download is finished all your contact files will be located in the **/vault/** folder, witch you can easily open with the [Obsidian](https://obsidian.md/) app.

**Note**: For automatic graph connections in Obsidian, you should configure your contacts to have a **'Related person'** field, that contains a connections name in format: **'[givenName] [familyName]'**. Also i highly encourage using **#tags** in notes field of your contacts, since all objects containing the same **#tag** will be also connected

#### Images

![Graph view 1](https://i.ibb.co/hKX29VG/graph-View1.png)

![Graph view 2](https://i.ibb.co/FHSDvT9/graph-View2.png)


## .md Template

A basic **t_person.md** template is included, but feel free to adapt or add new templates as per your requirements.

The script is compatible with [Jinja](https://jinja.palletsprojects.com/en/2.11.x/templates/) templates.

### Template fields

The object that's being used to fill out the templates is **'repo'**, so you can use:

```bash
{{ repo.organizations[0].title }} # to get the job title
{{ repo.organizations[0].name }}  # to get the company
```

Also, you can iterate through objects, e.g. one person having multiple phone numbers, also you can choose to skipp a section if a person doesn't have a phone number

```bash
{% if repo.phoneNumbers %}
Phones:
{% for phone in repo.phoneNumbers %}
    {% if phone.type %} {{phone.type}} | {% endif %}{{phone.value}}
{% endfor %}
{% endif %}
```

Example of a repo object with all properties can be found in repo_example.json

List of personFields used by this script:
- names
- emailAddresses
- organizations
- phoneNumbers
- biographies
- relations
- birthdays
- events
- addresses

For the complete list of template fields please reffer to [People API](https://developers.google.com/people/api/rest/v1/people/get)

## Note

It's crucial to follow the instructions for setting up the API key and ensure proper permissions before running the script.

This project is under development, so feel free to contribute and report issues or suggestions.

Enjoy connecting and visualizing your network!


