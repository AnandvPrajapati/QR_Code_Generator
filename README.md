# QR_Code_Generator
Generate QR code from URL


To run the provided code using ES modules, you can follow these steps:

### 1. Ensure Your Environment Supports ES Modules
First, ensure your Node.js environment supports ES modules by setting up your project correctly.

### 2. Set Up Your Project
1. **Initialize your project** (if you haven't already):
   ```bash
   npm init -y
   ```

2. **Add `"type": "module"` to your `package.json`**:
   Open `package.json` and add `"type": "module"` at the top level:
   ```json
   {
     "name": "your-project-name",
     "version": "1.0.0",
     "type": "module",
     "main": "index.js",
     "scripts": {
       "start": "node index.js"
     },
     "dependencies": {
       "inquirer": "^8.2.0",
       "qr-image": "^3.2.0"
     }
   }
   ```

3. **Install the required packages**:
   ```bash
   npm install inquirer qr-image fs
   ```

### 3. Write Your Code in `index.js`
Save your code in a file named `index.js`:

```javascript
import inquirer from "inquirer";
import qr from "qr-image";
import fs from "fs";

inquirer
    .prompt([
        {
            message: "Enter Your URL",
            name: "URL"
        }
    ])
    .then((answers) => {
        const url = answers.URL;
        var qr_svg = qr.image(url);
        qr_svg.pipe(fs.createWriteStream('qr-img1.png'));
    })
    .catch((error) => {
        if (error.isTtyError) {
            console.error("Prompt couldn't be rendered in the current environment.");
        } else {
            console.error("Something went wrong.");
        }
    });
```

### 4. Run Your Code
To run your code, use the following command:
```bash
npm start
```

This will execute your `index.js` file, prompt you for a URL, generate a QR code image, and save it as `qr-img1.png` in your current directory.

### Additional Notes
- Ensure you have Node.js installed (preferably the latest stable version).
- If you encounter any permission issues when creating the file, make sure you have write access to the directory.

This setup ensures that your code runs smoothly using ES modules with Node.js.
