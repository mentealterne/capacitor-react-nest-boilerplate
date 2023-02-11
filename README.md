# Popularise mobile app

This is the main popularise client app. It is a ionic app wrapped by capacitor and written in react + typescript.

## Steps to run the repo in a local environment

Be sure to have node v16 in your local environment

Install ionic cli globally:

`npm install -g @ionic/cli`

Install node_modules:

`npm install`

place in the root of this project an `.env` file (the .env file is stored for security reasons in Popularise 1Password account


Run the app via web for development purposes (with hotreload) with:

`ionic serve`


Build the app for ios and android with:

`ionic build`

`npx cap sync` (to sync podfiles and android packages)


Serve the builded version of the app in your local machine with:

`ionic build serve`


Consider that native plugins are not available via web browser, in this case you should connect an android or ios device to your local machine.

### Running in development mode with Android

1) Be sure to have the latest version of Android Studio installed

2) run `ionic cap run android  --external --livereload` from the root of your project and then choose an emulator or a connected physical device


### Running in development mode with IOS

1) Be sure to have xcode installed in your mac.

2) run `ionic cap run ios  --external --livereload` and choose your connected iphone or emulator



