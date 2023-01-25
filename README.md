# capacitor-react-nest-boilerplate(beta)

This is a basic monorepo boilerplate to quickly get started with Ionic/Capacitor using React and a Nestjs backend, everything in a Typescript fashion.\
It uses yarn workspaces to easily build all packages dependencies and docker to build packages images.\
Also, a docker-compose file is provided to speed up the development bootstrap and get things going faster.


## Steps to run the repo

### Development

`docker-compose up --build` 


or


`yarn install`\
`yarn start:client` to start Ionic app\
`yarn start:server` to start Nestjs backend




Remember to replace all occurrencies of `capacitor-react-nest-boilerplate` with your app name.
