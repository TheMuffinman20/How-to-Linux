# How do you choose the right desktop environment?

This guide helps you choose a suitable graphical workspace for your Linux installation. Your desktop environment is a complete package that includes a window manager, taskbar, file manager, settings, and default applications. The choice mainly affects usability, memory usage, and how much you need to configure yourself.

A **desktop environment** (DE) also includes a **window manager**, which mainly manages the application windows on your screen. This has a major influence on ease of use, the learning curve, and speed.

## 1. Consistency

The desktop should remain predictable and reliable.

- Do the settings and shortcuts work as expected?
- Are the components well integrated?
- Do you get regular updates without the entire workspace changing or breaking?

## 2. Flexibility

Each desktop offers a different balance between ease of use and control.

- Do you mainly want to work immediately, or configure everything yourself?
- Do you prefer a mouse, keyboard shortcuts, or a combination?
- Do you want to customize themes, panels, and window layouts extensively?

## 3. Performance

A heavy desktop uses more memory and graphical resources than a lightweight one.

- How much RAM does your system have?
- Do you prefer a calm environment or speed and performance?
- A tiling window manager can be light and fast, but usually requires more manual configuration.

_________________________________________________________________________________________________________________________________
| Desktop environment | Ease of use | Customizability | Performance | Suitable for | Notes |
| --- | --- | --- | --- | --- | --- |
| Cinnamon | High | Medium | Medium | Beginners, Windows users | Familiar, classic desktop with a lot of recognition |
| KDE Plasma | High | Very high | Medium | Users who want a lot of customization | Full desktop with many settings |
| GNOME | High | Low to medium | Medium | Beginners, users who want clarity | Modern, calm interface with little distraction |
| Xfce | High | Medium | Good | Older computers, users who want light use | Light and stable desktop |
| LXQt | Medium | Low | Very good | Limited hardware, lightweight systems | Minimalistic and fast desktop |
| Hyprland | Low | Very high | Very good | Power users, keyboard-driven workflows | Dynamic tiling window manager without a standard desktop |
| Sway | Low | High | Very good | Users who work like i3 | Light and fast, but more configuration needed |
| DWM | Very low | Very high | Very good | Advanced users | Extremely minimalistic and technical, few out-of-the-box features |

## Types of desktop environments

### Cinnamon

<img src="../../images/Desktops/Cinnamon_logo.png" alt="Cinnamon" width="100">

Cinnamon uses a familiar layout with a menu, taskbar, and system tray.

- Very accessible for Windows users
- Easy to understand
- Good balance between ease of use and features
- Heavier than the lightest desktop environments

Choose Cinnamon if you want to switch from Windows to Linux without major changes.

### KDE Plasma

<img src="../../images/Desktops/KDE_Plasma_logo.png" alt="KDE Plasma" width="100">

KDE Plasma offers a traditional desktop with many options for customizing appearance and behavior.

- Many settings and customization options
- Suitable for users coming from Windows
- Good support for multiple monitors and different workflows
- The many options can feel overwhelming

Choose KDE Plasma if you want a complete desktop that you can customize extensively.

### GNOME

<img src="../../images/Desktops/Gnome_logo.png" alt="Gnome" width="100">

GNOME has a simple and calm interface with a strong focus on clarity and workflow.

- Modern Wayland support
- Little distraction and a consistent interface
- Suitable for beginners
- Fewer settings and traditional taskbar options than some other desktops

Choose GNOME if you want a modern environment that works mostly simply and clearly.

### Xfce

<img src="../../images/Desktops/Xfce_logo.png" alt="Xfce" width="100">

Xfce is a lightweight and classic desktop environment.

- Low memory usage
- Stable and clear
- Suitable for older computers
- Less modern appearance and fewer integrated features than GNOME or KDE Plasma

Choose Xfce if performance and stability matter more than a modern default interface.

### LXQt

<img src="../../images/Desktops/LXQt_logo.png" alt="LXQt" width="100">

LXQt is designed to use as few system resources as possible.

- Very light
- Suitable for older or limited hardware
- Traditional desktop layout
- Fewer features and less integration by default

Choose LXQt if your computer has little memory or limited graphics performance.

### Hyprland

<img src="../../images/Desktops/Hyprland_logo.png" alt="Hyprland" width="100">

Hyprland is a dynamic window manager for Wayland. Windows are arranged automatically, and the workflow is strongly keyboard-driven.

- **Not suitable for new users**
- Flexible layout and extensive configuration
- Modern Wayland foundation
- Efficient for users who work with keyboard shortcuts
- No full desktop environment; panels, notifications, and other components often need to be set up separately
- Less suitable if you want a fully configured desktop immediately

Choose Hyprland if control, speed, and customization are important to you. You are also willing to build your workspace yourself.

### Sway

<img src="../../images/Desktops/Sway_logo.png" alt="Sway" width="100">

Sway is a minimalist dynamic window manager and compositor for Wayland. The configuration and shortcuts are largely compatible with i3, so existing i3 configurations can often serve as a starting point.

- **Not suitable for beginners**
- Light, stable, and efficient
- Familiar i3-like workflow with keyboard shortcuts
- Fewer visual effects and default features than Hyprland
- No full desktop environment; panels, notifications, and other components often need to be set up separately
- Suitable for users who want a simple Wayland workflow

Choose Sway if you want a light and stable Wayland window manager with an i3-like configuration and workflow.

### Dwm

<img src="../../images/Desktops/Dwm_logo.png" alt="Dwm" width="100">

Dwm is a minimalist and dynamic window manager for X11. Windows are arranged automatically, and control is primarily based on keyboard shortcuts.

- **Not suitable for beginners**
- Very light and fast
- Simple base without unnecessary features
- Configuration is usually done by modifying the source code and recompiling dwm
- Suitable for users who want to define their workflow completely themselves
- Panels, launchers, notifications, and other components often need to be installed separately

Choose dwm if you want an extremely light, keyboard-driven window manager and do not mind managing technical configuration yourself.

## Which desktop fits me?

### Quick choice
- If you want a Windows-like experience: Cinnamon or KDE Plasma
- If you want to work quickly and lightly: Xfce or LXQt
- If you want a lot of control: Hyprland, Sway, or DWM
- If you want a modern, calm environment: GNOME

### Windows users and beginners

Choose **Cinnamon** or **KDE Plasma**.

- **Cinnamon** has a simple and familiar layout, similar to the classic Windows environment.
- **KDE Plasma** has more features and customization options, like the modern Windows environment.

### Stability

Choose **GNOME** or **Xfce**.

- **GNOME** is suitable for a modern and integrated workflow.
- **Xfce** is better if you want a light and classic desktop environment.

### Performance

Choose **Hyprland** or **Dwm**.

- **Hyprland** works with Wayland and keyboard shortcuts.
- **Dwm** is a very minimalistic but fast tiling window manager.

> [!IMPORTANT]
> Keep in mind that after installation, you will need to install and configure your own taskbar, app launcher, notification system, background programs, and lock screen.

## Recommended choice

In this workshop, we choose **KDE Plasma**, because this desktop environment offers a good balance between ease of use, performance, and customizability.

If your distribution asks for a desktop environment during installation, choose **KDE Plasma**. You will then get a complete graphical desktop immediately, including a taskbar, file manager, settings, and support for multiple screens. For KDE Plasma, depending on your distribution, you can choose between a Wayland session and an X11 session.

> [!WARNING]
> Choose **No desktop environment** only if you deliberately want to install a window manager and the other parts of your workspace yourself.
