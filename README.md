# phoenix_elm_template
Instructions for setting up a Phoenix app with an Elm frontend

```
git clone https://github.com/noklesta/phoenix_elm_template.git

mix phoenix.new myapp
cd myapp
mix ecto.create
rm brunch-config.js
cp ../phoenix_elm_template/.gitignore .
cp ../phoenix_elm_template/package.json .
cp ../phoenix_elm_template/webpack.config.js .
yarn

rm web/static/css/app.css
cp ../phoenix_elm_template/app.scss web/static/css/
cp ../phoenix_elm_template/app.js web/static/js
cp ../phoenix_elm_template/index.html.eex web/templates/page
rm web/templates/layout/app.html.eex

mkdir web/static/elm
cd web/static/elm
elm-package install elm-lang/html
echo module Main exposing (..)\\n\\nimport Html exposing (..)\\n\\nmain : Html msg\\nmain = div [] [ text \"testing\" ] > Main.elm
cd ..
cp ../../../phoenix_elm_template/index.html .
```

Comment out watchers and live_reload in dev.exs

In router.ex, add this plug in pipeline :browser:
```
    plug :put_layout, false
```

In terminal 1:
mix phoenix.server

In terminal 2:
npm start
