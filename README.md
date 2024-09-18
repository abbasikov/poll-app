
# Poll App

This is a **Django Poll App** that allows users to create, edit, and vote on polls. The app includes user authentication (registration, login, and logout) and several poll-related features, such as creating new polls, adding choices, editing/deleting polls and choices, and ending polls.

## Features

### User Authentication:
- **Login**: Users can log in to their account to create or participate in polls.
- **Logout**: Users can log out of their account.
- **Registration**: New users can register by providing a username, password, and email. Validation checks for existing usernames and emails.

### Poll Management:
- **Create a Poll**: Authenticated users can create polls with choices. A user can create multiple polls.
- **Edit Polls**: Users can update their own polls, including adding or editing choices.
- **Delete Polls**: Users can delete their own polls.
- **End Poll**: Poll creators can end polls, making them read-only.
- **View Poll Results**: Once a poll is completed, users can view the results of the poll.
- **Vote**: Users can vote in active polls.

### Poll Voting:
- **Vote Once Per Poll**: Each user can vote only once per poll.
- **Choice Validation**: A user must select a choice before submitting a vote.

### Poll Listings:
- **Filter and Search**: Users can search for polls by title and sort by date, votes, and name.
- **Pagination**: Polls are paginated, showing a limited number of polls per page.

## Technologies Used

- **Django**: As the main framework for the application.
- **Django Templates**: For rendering HTML and creating dynamic content.
- **Bootstrap**: For front-end design and responsive layout.
- **SQLite**: For the database (default setup, can be changed).

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/abbasikov/poll-app.git
cd poll-app
```

### 2. Install Dependencies

Create a virtual environment and install the dependencies:

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Run Migrations

Apply database migrations:

```bash
python manage.py migrate
```

### 4. Create a Superuser (optional)

You can create a superuser to manage polls through the admin panel:

```bash
python manage.py createsuperuser
```

### 5. Start the Development Server

Run the local Django server:

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

## Application Flow

### User Authentication
- Users must be authenticated to create, edit, or delete polls.
- Non-authenticated users can view polls but cannot vote or manage them.

### Polls Management
- **Create Poll**: Only logged-in users can create new polls.
- **Poll Details**: Users can view the details of any poll.
- **Vote**: Users can vote on the poll. Each user is allowed only one vote per poll.

### Poll Lifecycle
1. **Poll Creation**: A user creates a poll with at least two choices.
2. **Voting**: Users vote on the poll.
3. **End Poll**: The poll creator can end the poll, making it read-only.

### Permissions
- **Poll Creation**: Users with the necessary permission can create polls.
- **Poll Editing**: Only the owner of the poll can edit or delete it.
- **Choice Management**: The poll creator can add, edit, or remove choices for their polls.

## Available Endpoints

### Accounts:
- `/accounts/login/` - User login page.
- `/accounts/logout/` - Logout the current user.
- `/accounts/register/` - Register a new user.

### Polls:
- `/polls/` - List all polls (with pagination).
- `/polls/<poll_id>/` - View poll details.
- `/polls/add/` - Add a new poll.
- `/polls/edit/<poll_id>/` - Edit an existing poll.
- `/polls/delete/<poll_id>/` - Delete a poll.
- `/polls/end/<poll_id>/` - End a poll.
- `/polls/vote/<poll_id>/` - Vote on a poll.

## Forms

- **UserRegistrationForm**: Handles user registration (username, password, email).
- **PollAddForm**: Used to create a new poll, including choices.
- **EditPollForm**: Used to edit an existing poll.
- **ChoiceAddForm**: Used to add or edit a poll choice.

## Permissions

- Only authenticated users can create, edit, and delete polls.
- Only the poll owner can modify or delete their polls and choices.
- Users need permission to add new polls (`polls.add_poll`).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.