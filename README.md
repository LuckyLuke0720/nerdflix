# nerdflix

## Project setup
```
npm install
```
## Dependencies
```
npm install bootstrap-icons
npm install bootstrap-icons-vue
npm install -g @vue/cli
```

## If there are issues with the ESLint parser
```
npm install --save-dev @babel/eslint-parser
```
## Encountered problems
I had an insanely annoying issue with the JSON parser that ate a lot of my time (close to 2 hours). It was due to the location of the JSON file.
With more time, I could have implemented the design closer to the Figma by using different UI/UX libraries, such as MaterialUI.

## Testing
After setting up and running the Vue project, you can switch between the "HomePage", "Series" and "Movies" sections, as shown in the Figma design. However, as the JSON file was not separated between movies and series, there was no way to differentiate between them and the buttons cause only visual changes.

You can search movies based on the title, by typing in the searchbar. On hovering over the movie's poster, the ImDB rating is shown as an overlay. Because some of the poster URLs don't work, the feature only applies to movies that have the URLs active.

The filters are present, but not functional. Without the challenges they would've worked, as I have implemented this exact feature in a different project of mine.

The like system is not operational. It would be implemented by having a liked prop in each MovieCard that sets to true if the users presses the like button linked to each MovieCard. Based on this prop, it would've been possible to show a list of liked movies.

### Compiles and hot-reloads for development
```
npm run serve
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
