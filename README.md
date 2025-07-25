# **LunaR** 🌘  

*A sleek, customizable fork of Moonwalk-Hugo with enhanced portfolio features*  

![LunaR-Hugo Preview](images/tn.png)  

**LunaR-Hugo** is a refined fork of [Moonwalk-Hugo](https://github.com/ArkhamCookie/moonwalk-hugo), preserving its minimalist design while adding powerful customization options—especially for portfolios and dynamic content.  

➡️ **Live Demo**: *[Coming Soon!]*  

---

## **✨ Key Features**  
✅ **All original Moonwalk features**:  
- Light/dark theme (auto-switch + manual toggle)  
- Responsive, mobile-friendly design  
- Data-driven content (via `data/` configs)  
- RSS feed & GitHub Pages compatibility  

🚀 **LunaR-Hugo improvements**:  
- **Markdown support in portfolio descriptions** (add images, links, formatting)  
- **Customizable section headers** (via `config.toml`)  
- **Flexible project status labels** (replace WIP boolean with any status)  
- **Semantic naming** (e.g., "Showcase" instead of "Portfolio")  

---

## **⚡ Quick Start**  

### **1. Install Hugo**  
Follow Hugo's [Quick Start guide](https://gohugo.io/getting-started/quick-start/) to install Hugo.  

### **2. Create a new site**  
```sh
hugo new site my-site && cd my-site
```

### **3. Add LunaR-Hugo**  
#### **Option A: Git Clone**  
```sh
git clone https://github.com/narnacle/lunar-hugo themes/lunar-hugo
```  
#### **Option B: Git Submodule**  
```sh
git submodule add https://github.com/narnacle/lunar-hugo themes/lunar-hugo
```  

### **4. Set the theme**  
Add to `hugo.toml`:  
```toml
theme = 'lunar-hugo'
```  

### **5. Run the dev server**  
```sh
hugo server -D
```  

---

## **🔧 Configuration**  

### **1. Custom Status Labels**  
Replace the old WIP boolean with any status text:  
```toml
[projects.1]
  title = "Web App"
  status = "Beta"  # Shows as colored badge
  url = "https://example.com"
  description = "In testing phase"
```

Predefined status styles: `WIP`, `Beta`, `Launched`, `On Hold`  
(Custom statuses auto-adapt to theme colors)

### **2. Customize Section Headers**  
In `data/config.toml`:  
```toml
[home]
  portfolio_title = "Showcase"   # Rename "Portfolio"
  blog_title = "Musings"        # Rename "Blog" 
  old_projects_title = "Archive" # Rename "Old Projects"
```  

### **3. Enable Markdown in Portfolios**  
```toml
[projects.2]
  title = "Mobile App"
  description = """
  **Featured Work!**  
  ![Screenshot](/img/app.png)  
  Built with Flutter.
  """
```

### **4. Toggle Sections**  
```toml
[home]
  portfolio = true      # Show portfolio
  blog = false         # Hide blog
  old_projects = true  # Show old projects
```  

---

## **🌌 Why LunaR-Hugo?**  
This fork enhances Moonwalk with:  
- **More expressive portfolios** (Markdown + images)  
- **Flexible project status system** (any label, not just WIP)  
- **Customizable section headers**  
- **Smoother customization** (via `config.toml`)  

---

## **📜 Credits & Attribution**  
- Original [Moonwalk-Hugo](https://github.com/ArkhamCookie/moonwalk-hugo) by ArkhamCookie  
- Based on [Moonwalk](https://github.com/abhinavs/moonwalk) by Abhinav Saxena  
- Light/dark toggle inspired by [Whitep4nth3r](https://whitep4nth3r.com/)  

---

## **🚧 Roadmap**  
- [ ] Add demo site  
- [ ] Support Hugo Modules  
- [ ] Expand blog layouts (grid, masonry)  

**Contributions welcome!** 🌟  

---

### Changelog  
**v0.2**: Added customizable status labels  
**v0.1**: Initial fork with Markdown support and header customization  
