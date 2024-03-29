# Environments

We have 11 total environments:
- **production** - our primary environment that is live to students
- **pre-production** - for testing large project deployment processes
- **beta-testing** - for beta testing projects to internal staff or students
- **web-staging-one** - for general purpose website testing, review, etc
- **web-staging-two** - for general purpose website testing, review, etc
- **web-staging-three** - for general purpose website testing, review, etc
- **web-staging-four** - for general purpose website testing, review, etc
- **web-staging-five** - for general purpose website testing, review, etc
- **app-staging-one** - for general purpose mobile app API testing, review, etc
- **app-staging-two** - for general purpose mobile app API testing, review, etc
- **app-staging-three** - for general purpose mobile app API testing, review, etc

Each environment deploys a specific branch in the musora-web-platform repository under the same name as the environment 
**except for 'production' which deploys the 'master' branch**.

## Web URLs

- [https://www.musora.com/](https://www.musora.com/)
- [https://pre-production.musora.com/](https://pre-production.musora.com/)
- [https://beta-testing.musora.com/](https://beta-testing.musora.com/)
- [https://web-staging-one.musora.com/](https://web-staging-one.musora.com/)
- [https://web-staging-two.musora.com/](https://web-staging-two.musora.com/)
- [https://web-staging-three.musora.com/](https://web-staging-three.musora.com/)
- [https://web-staging-four.musora.com/](https://web-staging-four.musora.com/)
- [https://web-staging-five.musora.com/](https://web-staging-five.musora.com/)
- [https://app-staging-one.musora.com/](https://app-staging-one.musora.com/)
- [https://app-staging-two.musora.com/](https://app-staging-two.musora.com/)
- [https://app-staging-three.musora.com/](https://app-staging-three.musora.com/)

# How To Deploy

## Any Staging/Testing/Beta/Pre Environment
To deploy any environment except production, push to the branch. GitHub actions automatically deploys the branch
anytime new changes are pushed. This usually takes around 5 minutes.

## Production
Coming soon...