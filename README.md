# 🔐 Password Strength Checker + Leak Lookup

A modern, privacy-focused password security tool that checks password strength locally and queries the HaveIBeenPwned API to detect compromised passwords using k-anonymity.

## 🌟 Features

### 🔒 **Local Password Strength Analysis**

- Real-time password strength assessment
- Visual strength meter with smooth animations
- Comprehensive criteria checking:
  - Minimum 8 characters
  - Uppercase & lowercase letters
  - Numbers and special characters
  - Detection of common passwords

### 🌐 **Privacy-First Breach Detection**

- Integration with HaveIBeenPwned API using k-anonymity
- Only sends first 5 characters of SHA-1 hash (never your actual password)
- Fallback to demo database for CORS-restricted environments
- Shows exact breach counts when compromised passwords are detected

### 🎨 **Modern UI/UX**

- Glassmorphism design with gradient backgrounds
- Smooth animations and micro-interactions
- Fully responsive design
- Dark mode friendly
- Accessibility compliant (WCAG 2.1)

## 🚀 Live Demo

[View Live Demo](https://zeeshan01001.github.io/PassGuardian)



## 🛠️ Technical Implementation

### **Security Features**

- **Client-side processing**: Passwords never leave your browser
- **SHA-1 hashing**: Uses Web Crypto API for secure hashing
- **K-anonymity**: Privacy-preserving API queries (only partial hashes sent)
- **No data storage**: Zero persistence of sensitive information
- **HTTPS ready**: Secure deployment compatible

### **Code Quality**

- **Vanilla JavaScript**: No external dependencies
- **Modern ES6+**: Async/await, arrow functions, template literals
- **Error handling**: Graceful fallbacks for network issues
- **Performance optimized**: Debounced input, efficient DOM updates
- **Accessibility**: ARIA labels, keyboard navigation, screen reader support

## 🏃‍♂️ Quick Start

### **Option 1: GitHub Pages (Recommended)**

1. Fork this repository
2. Enable GitHub Pages in repository settings
3. Visit `https://zeeshan01001.github.io/PassGuardian`

### **Option 2: Local Development**

```bash
# Clone the repository
git clone https://github.com/Zeeshan01001/PassGuardian.git
cd PassGuardian

# Serve locally (Python 3)
python -m http.server 8000

# Or with Node.js
npx serve .

# Visit http://localhost:8000
```

### **Option 3: Direct Download**

- Download `index.html`
- Open in any modern web browser
- No server required for basic functionality

## 🧪 Testing

### **Try These Examples**

- **Weak passwords**: `password`, `123456`, `qwerty`
- **Strong passwords**: `MyS3cur3P@ssw0rd!`, `Tr0ub4dor&3`
- **Check the difference**: See how breach detection works

### **Expected Behavior**

- Weak passwords should show as compromised with breach counts
- Strong, unique passwords should show as safe
- All strength criteria should update in real-time

## 🔧 Customization

### **Modify Strength Criteria**

```javascript
// In the checkPasswordStrength function
const criteria = {
    length: password.length >= 12,        // Increase minimum length
    uppercase: /[A-Z]/.test(password),
    lowercase: /[a-z]/.test(password),
    number: /\d/.test(password),
    special: /[!@#$%^&*()_+\-=\[\]{};':"\\|,.<>\/?~`]/.test(password),
    common: !commonPasswords.has(password.toLowerCase()),
    // Add new criteria
    noSequential: !/(?:abc|bcd|cde|def|efg|fgh|ghi|hij|ijk|jkl|klm|lmn|mno|nop|opq|pqr|qrs|rst|stu|tuv|uvw|vwx|wxy|xyz|012|123|234|345|456|567|678|789)/i.test(password)
};
```

### **Update Color Scheme**

```css
:root {
    --primary-gradient: linear-gradient(135deg, #your-color1, #your-color2);
    --color-success: #your-success-color;
    --color-danger: #your-danger-color;
    /* ... other variables */
}
```

### **Add More Common Passwords**

```javascript
const commonPasswords = new Set([
    // Add your domain-specific common passwords
    'yourcompany123',
    'yourcompany2024',
    // ... existing passwords
]);
```

## 🚀 Deployment

### **GitHub Pages**

1. Push code to `main` branch
2. Go to Settings → Pages
3. Select "Deploy from a branch"
4. Choose `main` branch, `/ (root)`
5. Save and wait for deployment

### **Netlify**

1. Connect your GitHub repository
2. Build settings: Leave empty (static site)
3. Deploy directory: `/` (root)
4. Deploy!

### **Vercel**

```bash
npm i -g vercel
vercel --prod
```

### **Custom Server**

- Simply upload `index.html` to any web server
- Ensure HTTPS for production use
- Consider adding security headers

## 🛡️ Security Considerations

### **What This Tool Does**

✅ Checks password strength locally  
✅ Uses privacy-preserving API queries  
✅ Provides real breach data  
✅ Never stores or transmits passwords  
✅ Works offline for strength checking  

### **What This Tool Doesn't Do**

❌ Replace proper password managers  
❌ Guarantee future security  
❌ Check against all possible breaches  
❌ Provide password generation  
❌ Work without JavaScript  

### **Best Practices**

- Use unique passwords for every account
- Enable 2FA/MFA whenever possible
- Use a reputable password manager
- Regularly update compromised passwords
- Consider passphrase-based passwords

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### **Bug Reports**

- Use the issue template
- Include browser version and OS
- Provide steps to reproduce
- Add screenshots if applicable

### **Feature Requests**

- Check existing issues first
- Describe the use case clearly
- Consider backwards compatibility
- Suggest implementation approach

### **Code Contributions**

```bash
# Fork the repo and create a feature branch
git checkout -b feature/amazing-feature

# Make your changes
# Add tests if applicable
# Update documentation

# Commit with conventional commits
git commit -m "feat: add amazing feature"

# Push and create a Pull Request
git push origin feature/amazing-feature
```

### **Development Guidelines**

- Keep it vanilla JS (no frameworks)
- Maintain accessibility standards
- Test in multiple browsers
- Follow existing code style
- Update README if needed

## 📊 Browser Support

| Browser | Version | Status         |
| ------- | ------- | -------------- |
| Chrome  | 63+     | ✅ Full support |
| Firefox | 57+     | ✅ Full support |
| Safari  | 11.1+   | ✅ Full support |
| Edge    | 79+     | ✅ Full support |
| Opera   | 50+     | ✅ Full support |

### **Required Features**

- Web Crypto API (for SHA-1 hashing)
- Fetch API (for breach checking)
- ES6+ support (async/await, arrow functions)

## 🐛 Known Issues

- **CORS limitations**: Some browsers may block API requests in local development
- **Rate limiting**: HaveIBeenPwned API has rate limits (1 request per 1.5 seconds)
- **Mobile Safari**: Minor visual glitches in landscape mode
- **Internet Explorer**: Not supported (requires modern browser features)

## 📈 Performance

- **First Load**: ~50KB total (HTML + CSS + JS)
- **Subsequent loads**: Cached (0 bytes)
- **API Response**: Typically 1-5KB per breach check
- **Memory usage**: <10MB typical
- **CPU usage**: Minimal (client-side hashing is fast)

## 🔮 Future Enhancements

### **Planned Features**

- [ ] Password generation with customizable rules
- [ ] Batch password checking
- [ ] Export/import functionality
- [ ] Internationalization (i18n)
- [ ] Progressive Web App (PWA) support
- [ ] Advanced entropy calculation
- [ ] Integration with more breach databases

### **Under Consideration**

- [ ] Browser extension version
- [ ] API endpoint for developers
- [ ] Dark/light theme toggle
- [ ] Password strength evolution over time
- [ ] Machine learning-based predictions

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2024 Zeeshan

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## 🙏 Acknowledgments

- **HaveIBeenPwned**: For providing the breach detection API
- **Troy Hunt**: For creating and maintaining HaveIBeenPwned
- **Web Crypto API**: For enabling client-side cryptography
- **GitHub Pages**: For free hosting
- **Community**: For feedback and contributions

## 📞 Support

- **Documentation**: Check this README first
- **Issues**: Use GitHub Issues for bugs/features
- **General**: Discussions tab for questions

---

### 🌟 Star this repo if you find it helpful!

**Made with ❤️ for better password security**