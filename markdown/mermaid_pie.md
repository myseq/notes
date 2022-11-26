# Pie Chart Samples

| Theme    | Description |
| :----    |  :--------- |
| `base`    |  Designed to be modified, as the name implies it is supposed to be used as the base for making custom themes. |
| `forest`  |  A theme full of light greens that is easy on the eyes. |
| `dark`    |  A theme that would go well with other dark-colored elements. |
| `default` |  The default theme for all diagrams. |
| `neutral` |  The theme to be used for black and white printing. |


### DarkMode Base Theme
```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'darkMode': 'true' }}}%%
pie
    title Dark | Base
    "Movies" : 20
    "TV shows" : 80
```

### DarkMode Custom Theme
```mermaid
%%{init: {
    'theme': 'base',
    'themeVariables': {
        'primaryColor': '#ffbf00',
        'primaryBorderColor': '#78e2a0',
        'secondaryColor': '#78e2a0',
        'primaryBorderColor': '#ffbf00',
        'darkMode': 'true' }}}%%
pie showData
    title Dark | Custom
    "Major" : 61.8
    "Minor" : 38.2
```

