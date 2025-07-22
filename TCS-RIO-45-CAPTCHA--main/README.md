# TCS-RIO-45-CAPTCHA Service

A Java web application that implements a CAPTCHA service to secure web-based applications. This project demonstrates how to build a complete CAPTCHA system with image generation, validation, and modern UI.

## 🎯 Project Overview

This CAPTCHA service provides:
- **Dynamic CAPTCHA Generation**: Creates 6-character alphanumeric CAPTCHA images
- **Image Distortion**: Adds random colored lines to make CAPTCHA harder to crack
- **Session-based Validation**: Secure validation using HTTP sessions
- **Modern UI**: Dark theme with responsive design
- **Error Handling**: Proper validation and error messages

## 🏗️ Project Structure

```
TCS-RIO-45-CAPTCHA--main/
├── CaptchaGenerator.java          # CAPTCHA image generation logic
├── CaptchaServlet.java           # Web servlet for handling requests
├── CaptchaProject/               # Web application directory
│   ├── index.jsp                 # Main form page
│   └── WEB-INF/
│       ├── web.xml               # Servlet configuration
│       └── classes/
│           └── com/captcha/      # Compiled Java classes
└── README.md                     # This file
```

## 🚀 Quick Start

### Prerequisites
- **Java JDK 8+** 
- **Apache Tomcat 9+**
- **Web Browser**

### Step 1: Download Dependencies
```bash
# Download servlet API
curl -o servlet-api.jar https://repo1.maven.org/maven2/javax/servlet/javax.servlet-api/4.0.1/javax.servlet-api-4.0.1.jar

# Download Apache Tomcat
curl -o apache-tomcat-9.0.85-windows-x64.zip https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.85/bin/apache-tomcat-9.0.85-windows-x64.zip
```

### Step 2: Compile Java Classes
```bash
javac -cp "servlet-api.jar" -d CaptchaProject/WEB-INF/classes CaptchaGenerator.java CaptchaServlet.java

```

### Step 3: Create WAR File
```bash
cd CaptchaProject
jar -cf captcha.war *
```

### Step 4: Deploy to Tomcat
```bash
# Extract Tomcat
Expand-Archive -Path "apache-tomcat-9.0.85-windows-x64.zip" -DestinationPath "." -Force

# Deploy WAR file
Copy-Item "CaptchaProject/captcha.war" "apache-tomcat-9.0.85/webapps/"
```

### Step 5: Start Tomcat Server
```bash
cd apache-tomcat-9.0.85/bin
.\startup.bat
```

### Step 6: Access Application
Open your browser and navigate to:
**http://localhost:8080/captcha/**

## 🎮 How to Use

1. **Fill the Form**: Enter your name and email address
2. **Proceed to CAPTCHA**: Click the submit button
3. **Solve CAPTCHA**: Enter the characters shown in the image
4. **Submit**: If correct, you'll see a success message

## 🔧 Features

### CAPTCHA Generation
- **6-character alphanumeric codes**
- **Excludes confusing characters** (0, O, 1, I, etc.)
- **Random distortion lines** for security
- **Anti-aliasing** for smooth text rendering

### Security Features
- **Session-based validation**
- **Case-sensitive matching**
- **Automatic regeneration** on failed attempts
- **No CAPTCHA reuse** between sessions

### UI/UX Features
- **Dark theme design**
- **Responsive layout**
- **Modern styling**
- **Error message display**
- **Form validation**

## 🛠️ Technical Details

### Java Classes

#### CaptchaGenerator.java
- `generateCaptchaText()`: Creates random 6-character strings
- `generateCaptchaImage()`: Renders CAPTCHA with distortion

#### CaptchaServlet.java
- Handles POST requests
- Manages session data
- Validates CAPTCHA input
- Generates HTML responses

### Web Configuration
- **Servlet mapping**: `/CaptchaServlet`
- **Session management**: Automatic session creation
- **Content type**: HTML responses with embedded CSS

## 🐛 Troubleshooting

### Common Issues

**Tomcat won't start:**
- Check if port 8080 is already in use
- Ensure Java is properly installed
- Verify Tomcat installation

**Compilation errors:**
- Make sure servlet-api.jar is in the classpath
- Check Java version compatibility

**Application not accessible:**
- Verify Tomcat is running on port 8080
- Check if WAR file is properly deployed
- Look for errors in Tomcat logs

### Logs Location
- **Tomcat logs**: `apache-tomcat-9.0.85/logs/`
- **Application logs**: Check Tomcat console output

## 🛑 Stopping the Application

```bash
cd apache-tomcat-9.0.85/bin
.\shutdown.bat
```

## 📝 Development

### Adding New Features
1. Modify Java source files
2. Recompile classes
3. Recreate WAR file
4. Redeploy to Tomcat

### Customization
- **CAPTCHA length**: Modify `generateCaptchaText()` method
- **Image style**: Update `generateCaptchaImage()` method
- **UI design**: Edit CSS in servlet responses
- **Validation logic**: Modify validation in `CaptchaServlet`

## 📄 License

This project is part of TCS iON RIO-45 course materials.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📞 Support

For issues and questions:
- Check the troubleshooting section
- Review Tomcat logs
- Verify all prerequisites are met

---

**Built with ❤️ for TCS iON RIO-45 Course**
