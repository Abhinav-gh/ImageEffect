# ImageEditor-Website

## Table of Contents

- [ImageEditor-Website](#imageeditor-website)
  - [Table of Contents](#table-of-contents)
  - [Overview](#overview)
  - [Image Editing Functionality](#image-editing-functionality)
  - [Backend Architecture](#backend-architecture)
  - [Key Features](#key-features)
  - [Challenges Faced](#challenges-faced)
  - [Acknowledgements](#acknowledgements)
  - [Image editor web app: Installation](#image-editor-web-app-installation)
  - [Backend setup](#backend-setup)
- [Frontend](#frontend)
  - [Overview](#overview-1)
  - [Technologies Used](#technologies-used)
  - [Frontend setup](#frontend-setup)
    - [1. Clone the repository:](#1-clone-the-repository)
    - [2. Install dependencies using npm:](#2-install-dependencies-using-npm)
    - [3. Navigate to the ImageEffectFrontend directory:](#3-navigate-to-the-imageeffectfrontend-directory)
    - [4. Start the development server:](#4-start-the-development-server)
    - [Code Scaffolding](#code-scaffolding)
    - [Build](#build)
    - [Running Unit Tests](#running-unit-tests)
    - [Running End-to-End Tests](#running-end-to-end-tests)
    - [Further Help](#further-help)
  - [Authors](#authors)

## Overview

ImageEditor-Website is a sophisticated web application designed for image manipulation, leveraging advanced technologies for both backend and frontend. The backend, powered by Spring Boot, seamlessly integrates with C++ libraries via JNI, ensuring high-performance image processing. MongoDB serves as the storage solution for effect logs, adding robustness to the application

## Image Editing Functionality

- **Hue Saturation:** Adjust the hue and saturation of images. 
- **Brightness:** Modify the brightness of images.
- **Contrast:** Change the contrast of images.
- **Flip:** Flip images horizontally or vertically.
- **Gaussian Blur:** Apply Gaussian blur to images.
- **Grayscale:** Convert images to grayscale.
- **Invert:** Invert colors of images.
- **Rotation:** Rotate images to the desired angle.
- **Sepia:** Apply a sepia tone to images.
- **Sharpen:** Enhance the sharpness of images.
- **Dominant Colour:** Identify and display the dominant color in images.

## Backend Architecture

The backend of ImageEditor-Website is powered by **Spring Boot**, providing a robust foundation for the application. 
- **JNI** (Java Native Interface) is used to access C++ libraries, ensuring fast and efficient image modification. 
- **MongoDB** is employed to store logs of the effects applied to images.

## Key Features
- **Modular Structure:** The frontend is organized into modular components, ensuring maintainability and scalability.

- **Responsive Design:** The user interface is designed to be responsive, catering to various screen sizes and devices.

- **Image Upload:** Users can effortlessly upload source images for applying diverse image effects.

- **Effect Application:** The frontend seamlessly communicates with the backend to apply effects such as brightness, contrast, rotation, and more.

- **Result Display:** The resulting images are dynamically displayed, allowing users to preview and download the edited images.

- **Download Functionality:** Users can download the edited images with ease using the provided download buttons.

- **User-friendly Interface:** The frontend is designed to be intuitive, enabling users to navigate and interact with the application effortlessly.

## Challenges Faced
- Maven was not working directly with 'mvn' command in some laptops.Hence we first installed dos2unix which helped us in using maven using the command './mvnw'
- After refreshing the logs page, the logs were disappearing. Hence, we felt the need of having a database to store the logs to make them persistent. Thus, we used Mongo DB as our database.
- Initially we were not able to integrate Mongo DB with our backend. We then cleaned and re installed the Maven project directory which solved the issue.
- The Dominant Colour effect was initially not present in the Makefile. We added the necessary statements in the Makefile to solve the issue. We made a new folder in the CPP libraries for the Dominant Colour effect. In that folder we made the DominantColourInterface.cpp file which has the required JNI code.
- Initially, we used Executors.callable() method to implement multithreading. However, it did not work. Thus, we switched to using Callable and Future to implement multithreading.
- The Flip effect and Hue Saturation have 2 values which are being POSTed by the frontend. However, in the baseEffects package, all the interfaces expected either a single value or no value. Thus, we felt the need to make 2 new interfaces : one for handling 2 discrete values (for Flip effect) and the other for handling 2 parameterizable values (for Hue Saturation effect).

## Acknowledgements
We would like to express our sincere gratitude to our professor and teaching assistants for their invaluable guidance and support throughout the completion of this project.

Additionally, we acknowledge and appreciate the following external resources that proved instrumental in the development of our project:

- https://docs.spring.io/spring-data/mongodb/docs/1.2.0.RELEASE/reference/html/mongo.repositories.html
- https://mvnrepository.com/artifact/org.springframework.boot/spring-boot-starter-data-mongodb
- https://www.baeldung.com/java-runnable-callable
- https://angular.io/api
- https://medium.com/@samuelcatalano/connecting-spring-boot-to-mongodb-a-step-by-step-guide-b9f2fd9e872d
- https://www.mongodb.com/compatibility/spring-boot

## Image editor web app: Installation


Clone the repository:

   ```bash
   git clone https://github.com/KetanGhungralekar/ImageEditor-Website
   ```
For setting up backend: [Skip to here](#backend-setup)   
For setting up frontend: [Skip to here](#frontend-setup)   


## Backend setup
Before proceeding with the backend setup, ensure you have the following prerequisites installed:

  If you are using windows you will need WSL
  + [Windows Subsystem for Linux (WSL)](https://docs.microsoft.com/en-us/windows/wsl/install)

+ [MongoDB](https://docs.mongodb.com/manual/installation/)

- Navigate to the backend folder.

   ```bash
   cd .\ImageEffectBackend\
   ```

- Start WSL.

   ```bash
   wsl
   ```
- Clean the project directory.

   ```bash
   make clean
  ```
- Run the Makefile.

   ```bash
   make
  ```
- Clean the Maven project directory.

   ```bash
   mvn clean
  ```
- Build the Maven package.

   ```bash
   mvn package
   ```
- Create a folder for running the Mongo DB server.

   ```bash
   mkdir mongo_database
   ```
- Open a new terminal and navigate to the recently made folder.

   ```bash
   cd .\ImageEffectBackend\mongo_database
   ```
- Run the Mongo DB server.

   ```bash
   mongod --dbpath . --port 27017
   ```
- Now open Mongo DB Compass GUI and press **CONNECT**.
- Now navigate to the first terminal.
- Run the SpringBoot backend server.

  ```bash
   java -jar target/driveProject-0.0.1-SNAPSHOT.jar
  ```

  This command executes the JAR file, which contains all the compiled Java classes and dependencies needed to run the Spring Boot application. Learn more about [Java JAR files](https://docs.oracle.com/javase/8/docs/technotes/tools/windows/jar.html).
- If something goes wrong, then run the following Maven command.

  ```bash
  mvn clean install
  ```
Return to [Installation](#image-editor-web-app-installation)





# Frontend

## Overview

The `ImageEffectFrontend` component is a robust Angular-based frontend (version 14.2.10) for the ImageEditor-Website, offering an intuitive and feature-rich interface for image editing. This section provides an overview of the project structure, key features, and technologies used.


## Technologies Used

- **Angular:** The frontend is built using the Angular framework, providing a modular and scalable architecture.

- **TypeScript:** The primary language used for building Angular applications, offering static typing for enhanced code reliability.

- **HTML and SCSS:** Structuring and styling the user interface for a seamless and visually appealing experience.

- **RxJS:** Utilized for handling asynchronous operations and events efficiently.

- **Angular Forms:** Employed for building dynamic and interactive forms, crucial for user input.

- **Angular Services:** Used to handle data and communication with the backend.

- **Angular Router:** Facilitates navigation within the application, enabling a smooth user experience.

- **DOM Sanitization:** Ensures the security of dynamically generated URLs and content.


## Frontend setup

### 1. Clone the repository:

```bash
git clone https://github.com/KetanGhungralekar/ImageEditor-Website
```

### 2. Install dependencies using npm:

```bash
npm install
```
### 3. Navigate to the ImageEffectFrontend directory:

```bash
cd .\ImageEffectFrontend\
```
### 4. Start the development server:

```bash
npm start
```
The application should be accessible at http://localhost:4200/ in your web browser.
Return to [Installation](#image-editor-web-app-installation)

### Code Scaffolding
Generate a new component using the following command:
```bash
ng generate component component-name
```

### Build
Run the following command to build the project. The build artifacts will be stored in the dist/ directory.
```bash
ng build
```

### Running Unit Tests
Execute the unit tests via Karma with the following command:
``` bash
ng test
```

### Running End-to-End Tests
Execute the end-to-end tests via a platform of your choice:
```bash
ng e2e
```

### Further Help
For more help on the Angular CLI, use the following command:
```bash
ng help
```
or you can go check out the [Angular CLI Overview and Command Reference](https://angular.io/cli)
page.

## Authors

- [Abhinav Deshpande](https://www.github.com/Abhinav-gh/)
- [Ketan Ghungralekar](https://www.github.com/KetanGhungralekar/)
- [Krish Dave](https://github.com/KrishDave1)
- [Valmik Belgaonkar](https://github.com/valmikGit)
- [Vedant Mangrulkar](https://github.com/MVedant21)


