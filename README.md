Jumber Boy

Introduction
Jumber Boy is a lite action game where players control a hero on a quest to save a princess. Developed using JavaScript, HTML5, CSS3, PHP, and MySQL, the game offers an engaging experience with smooth gameplay and intuitive controls. The project was created by Mohamed Ali, with a passion for game development and a desire to bring classic action game charm to modern audiences.

Deployed Site: Jumber Boy Game
Final Project Blog Article: Read the Full Development Journey
Author's LinkedIn: https://www.linkedin.com/in/mohamed-ali-103455b0
Installation
To run Jumber Boy locally, follow these steps:

Clone the Repository:

bash
Copy code
git clone https://github.com/yourusername/jumber-boy.git
cd jumber-boy
Install Dependencies:
This project does not require any additional dependencies beyond a web server for PHP. Ensure you have a local server setup like XAMPP, WAMP, or any other PHP server.

Setup the Database:

Create a MySQL database named jumber_boy.
Import the database schema from the db_schema.sql file included in the repository.
Run the Server:
Start your local PHP server and navigate to the project directory. Access the game through your browser at http://localhost/jumber-boy.

Usage
Once the game is running, use the following controls to play:

Arrow Keys: Move the character
Space Bar: Jump
Shift Key: Run
The objective is to navigate through various levels, overcome obstacles, and save the princess.

Contributing
Contributions to Jumber Boy are welcome! If you have suggestions, bug reports, or improvements, feel free to submit a pull request or open an issue.

Steps to Contribute:

Fork the repository.
Create a new branch: git checkout -b https://github.com/mohamedselem/Jumber.Boy.git
Make your changes and commit them: git commit -m 'Add some feature'
Push to the branch: git push origin feature/your-feature-name
Open a pull request.

Technical Details
Technology & Architecture
Frontend:

HTML5 & CSS3: Used for structuring and styling the game. The canvas element in HTML5 was crucial for rendering the game graphics.
JavaScript: The core language for game logic and interactivity. JavaScript allowed for real-time updates and responsive controls.
Backend:

PHP: Used for server-side scripting and handling game state management.
MySQL: The database system used to store player data and game progress.
Core Algorithms
Collision Detection
One of the critical components of Jumber Boy is the collision detection system. Initially, I implemented a simple bounding box algorithm. However, this approach was insufficient for complex shapes and resulted in inaccurate collisions.

To improve accuracy, I combined bounding box detection with pixel-perfect collision detection. The bounding box method quickly determines potential collisions, while pixel-perfect detection refines this by checking individual pixels within the overlapping areas.

Bounding Box Collision:

javascript
Copy code
function isColliding(a, b) {
    return (
        a.x < b.x + b.width &&
        a.x + a.width > b.x &&
        a.y < b.y + b.height &&
        a.y + a.height > b.y
    );
}
Pixel-Perfect Collision:

javascript
Copy code
function pixelPerfectCollision(sprite1, sprite2) {
    let ctx1 = sprite1.getContext('2d');
    let ctx2 = sprite2.getContext('2d');
    let imgData1 = ctx1.getImageData(0, 0, sprite1.width, sprite1.height).data;
    let imgData2 = ctx2.getImageData(0, 0, sprite2.width, sprite2.height).data;

    for (let i = 0; i < imgData1.length; i += 4) {
        if (imgData1[i + 3] !== 0 && imgData2[i + 3] !== 0) {
            return true;
        }
    }
    return false;
}
Data Flow Architecture
The architecture of Jumber Boy ensures smooth interaction between the frontend and backend. Here is a diagram that shows the flow of data through the application:


Player Input: User interactions are captured through keyboard events.
Game Logic: JavaScript processes these inputs, updates game state, and renders the game on the HTML5 canvas.
Server Communication: PHP handles data requests and interactions with the MySQL database.
Database Storage: MySQL stores player progress and game state information.
Features
Responsive Controls:

The game offers fluid and responsive controls using arrow keys for movement and space bar for jumping.
Dynamic Levels:

Each level is uniquely designed with increasing difficulty, providing a challenging yet enjoyable experience.
Save and Load Progress:

Players can save their progress and load it later, thanks to the backend integration with PHP and MySQL.
