# tractusx-edc-dashboard

This repository contains the Catena-X Policy Builder, which consists of the following components:
- The [eclipse-edc/DataDashboard](https://github.com/eclipse-edc/DataDashboard) as git submodule in the `eclipse-edc` folder to use the dashboard library.
- A minimal Tractus-X connector for policy validation in the `cx-policy-validator` folder. The connector implements a policy validation endpoint and adds it to the management API context.
- Everything else in this repo belongs to the Angular frontend (UI) of the Catena-X Policy Builder.

## Local Setup
1. Build and run the validator backend:
   - Docker:
     1. `cd cx-policy-validator`
     2. `docker build -t cx-policy-builder-validator .`
     3. `docker run --rm -p 8000:8000 -p 8010:8010 cx-policy-builder-validator`
   - Gradle:
     1. `cd cx-policy-validator`
     2. `./gradlew shadowJar`
     3. `java -Dedc.fs.config="tx-memory-connector/config.properties" -jar tx-memory-connector/build/libs/runtime.jar`
2. Build and run the UI:
   - Docker:
     1. `docker build -t cx-policy-builder-ui .`
     2. `docker run --rm -p 8080:8080 cx-policy-builder-ui`
     3. Open [http://localhost:8080](http://localhost:8080)
   - Angular DEV server:
     1. `npm run lib-build -- --configuration production`
     2. `npm run start`
     3. Open [http://localhost:4200](http://localhost:4200)
