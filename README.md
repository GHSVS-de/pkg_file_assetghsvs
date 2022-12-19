# PKG_FILE_ASSETGHSVS

Joomla file package. Different versions of asset files that I often need. For example, Bootstrap, JQuery, JQuery-Slim. The assets are stored in Joomla folder `/media/assetghsvs/`. Not more.

DE: See https://ghsvs.de/programmierer-schnipsel/sonstige/352-npm-mehrere-versionen-des-selben-pakets-in-node-modules

## New Bootstrap 5 release? Special step (1)!!!!! Build reduced `bootstrap.bundle` JS!!!!!!

- Delete everything in `/mnt/z/git-kram/bootstrap/`
  - but don't delete `./.git`!
  - but don't delete `./node_modules`!
- Get from https://github.com/twbs/bootstrap correct version:
  - Select in tags dropdown the wished release.
  - Download ZIP and unzip into `/mnt/z/git-kram/bootstrap/`.
- Open Github Desktop and let it do it's local work ("refresh with new files").
- `cd /mnt/z/git-kram/bootstrap/;unlink package-lock.json;rm -r dist/;rm -r js/dist/`
- `npm install`
- Change file `git-kram/bootstrap/js/index.umd.js`
- Comment out unwanted parts. Each twice.

```
import Alert from './src/alert'
import Button from './src/button'
// import Carousel from './src/carousel'
import Collapse from './src/collapse'
import Dropdown from './src/dropdown'
import Modal from './src/modal'
import Offcanvas from './src/offcanvas'
// import Popover from './src/popover'
// import ScrollSpy from './src/scrollspy'
// import Tab from './src/tab'
import Toast from './src/toast'
// import Tooltip from './src/tooltip'

export default {
  Alert,
  Button,
  // Carousel,
  Collapse,
  Dropdown,
  Modal,
  Offcanvas,
  // Popover,
  // ScrollSpy,
  // Tab,
  Toast,
  // Tooltip
}
```

- Compile: `npm run js`
  - Or: `npm run dist`

### !!!Don't forget then!!!
- `mkdir _ghsvsBootstrapBundleVersion_;cp js/index.umd.js _ghsvsBootstrapBundleVersion_`
- Copy following from `git-kram/bootstrap/dist/js` to `src\packages\file_assetghsvs\js\bootstrap\xy\-_custom_-` (`xy` is the BS version).
  - `/_ghsvsBootstrapBundleVersion_/` (I don't know if still needed in `tpl_bs4ghsvs` but good as reference what is included in bundle.js).
  - `bootstrap.bundle.js`
  - `bootstrap.bundle.js.map`
  - `bootstrap.bundle.min.js`
  - `bootstrap.bundle.min.js.map`

## Build package
- Prepare/adapt `./package.json`.
- `cd /mnt/z/git-kram/pkg_file_assetghsvs`
- `npm run updateCheck`
- `npm run update`
- `node build`
