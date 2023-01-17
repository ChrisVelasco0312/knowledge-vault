
## Getting started

`ctrl+b+d` Detach from the currentt session.
`tmux ls` List the active tmux sessions
`tmux a -t 0` Attach to session 0

### Basic commands

-   `ctrl + b + "`: Split the window horizontaly.
-   `ctrl + b + %`: Split the window into two panes vertically
-  `ctrl + b Arrows` Move between panes
-   `ctrl + b + o (1,2..)`: Move to specific window
-   `ctrl + b + space`: cambia entre los diferentes diseños de paneles disponibles.
-  `ctrl + b + ?` View all keybindings
-  `ctrl+w`  Open a panel to navigate across windows in multiple sessions.
-   `ctrl + b + z`: maximiza el panel actual y minimiza los demás paneles.

Para utilizar estos atajos de teclado, se debe presionar la tecla `ctrl` y la tecla `b` al mismo tiempo, y luego presionar la tecla que corresponda al atajo que se quiere usar. Por ejemplo, para dividir el panel actual en dos secciones verticalmente, se debe presionar `ctrl + b + "`.

### Configure tmux
`$HOME/.tmux.conf` Use this file to customize tmux
