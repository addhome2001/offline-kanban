
# Offline Kanban

_Kanban board that just works in your browser (even when you have no internet)_

[![Build Status](https://travis-ci.org/sarmadsangi/offline-kanban.svg?branch=master)](https://travis-ci.org/sarmadsangi/offline-kanban)

### Getting started
```javascript
npm install
npm run dev
```

### Production build
```javascript
npm run build
```

### Architecture (TODO)

I will be adding a dragram/details to explain architecture properly. Here is the few bullet points of architecture/tech stack,

1. View (ReactJS) responds to state changes (Mobx: state management)
2. Most of Kanban board logic (add cards, remove cards, add list, move cards to lists and etc) is in `stores/kanban.js`
3. Everytime state changes (in `KanbanStore`) it auto saves a snapshot of `KanbanBoard` state to `PouchDB (IndexedDB/WebSQL)`
4. All assets (including html) are cached in browser using `AppCache`, `Service Workers` look for any new changes and auto updates the cache / reload the browser (Todo: show a button to refresh).
5. Since `PouchDB` in this case is just storing everything locally the whole thing is available offline.
6. `CSS Modules` to avoid global conflicts and to decipline myself in writing css per component only.
7. `Travis` is used for CI and app is deployed to heroku automatically after CI passes. Check [![Build Status](https://travis-ci.org/sarmadsangi/offline-kanban.svg?branch=master)](https://travis-ci.org/sarmadsangi/offline-kanban)


### TODOS

1. Make it mobile friendly (components/controls specific to mobile)
2. Abstract store
3. Create decorators or contains for drag and drop operations
4. Improve sorting (it breaks from time to time)
5. Move from Card and List into either parent level container or store
6. Rename functions/variables to be more readible
7. Performance optimisations (too many filtering here and there)

