# Getting Started with Create React App

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Available Scripts

In the project directory, you can run:

### `npm start`

Runs the app in the development mode.\
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.\
You will also see any lint errors in the console.

### `npm test`

Launches the test runner in the interactive watch mode.\
See the section about [running tests](https://facebook.github.io/create-react-app/docs/running-tests) for more information.

### `npm run build`

Builds the app for production to the `build` folder.\
It correctly bundles React in production mode and optimizes the build for the best performance.

The build is minified and the filenames include the hashes.\
Your app is ready to be deployed!

See the section about [deployment](https://facebook.github.io/create-react-app/docs/deployment) for more information.

### `npm run eject`

**Note: this is a one-way operation. Once you `eject`, you can’t go back!**

If you aren’t satisfied with the build tool and configuration choices, you can `eject` at any time. This command will remove the single build dependency from your project.

Instead, it will copy all the configuration files and the transitive dependencies (webpack, Babel, ESLint, etc) right into your project so you have full control over them. All of the commands except `eject` will still work, but they will point to the copied scripts so you can tweak them. At this point you’re on your own.

You don’t have to ever use `eject`. The curated feature set is suitable for small and middle deployments, and you shouldn’t feel obligated to use this feature. However we understand that this tool wouldn’t be useful if you couldn’t customize it when you are ready for it.

## Learn More

You can learn more in the [Create React App documentation](https://facebook.github.io/create-react-app/docs/getting-started).

To learn React, check out the [React documentation](https://reactjs.org/).

### Code Splitting

This section has moved here: [https://facebook.github.io/create-react-app/docs/code-splitting](https://facebook.github.io/create-react-app/docs/code-splitting)

### Analyzing the Bundle Size

This section has moved here: [https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size](https://facebook.github.io/create-react-app/docs/analyzing-the-bundle-size)

### Making a Progressive Web App

This section has moved here: [https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)

### Advanced Configuration

This section has moved here: [https://facebook.github.io/create-react-app/docs/advanced-configuration](https://facebook.github.io/create-react-app/docs/advanced-configuration)

### Deployment

This section has moved here: [https://facebook.github.io/create-react-app/docs/deployment](https://facebook.github.io/create-react-app/docs/deployment)

### `npm run build` fails to minify

This section has moved here: [https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify](https://facebook.github.io/create-react-app/docs/troubleshooting#npm-run-build-fails-to-minify)

git remote add origin https://github.com/DJTechnologies/nucampweek3.git

compon.js

import React, { Component } from "react";
import {
Card,
CardImg,
CardText,
CardBody,
CardTitle,
Breadcrumb,
BreadcrumbItem,
} from "reactstrap";
import { Link } from "react-router-dom";

class CampsiteInfo extends Component {
renderCampsite(campsite) {
return (
<div className="col-md-5 m-1">
<Card>
<CardImg top src={campsite.image} alt={campsite.name} />
<CardBody>
<CardTitle>{campsite.name}</CardTitle>
<CardText>{campsite.description}</CardText>
</CardBody>
</Card>
</div>
);
}

renderComments(comments) {
if (comments) {
return (
<div className="col-md-5 m-1">
<h4>Comments</h4>
{comments.map((comments) => (
<div className="p-1" key={comments.id}>
{comments.text}
<br></br>
-- {comments.author},{" "}
{new Intl.DateTimeFormat("en-US", {
year: "numeric",
month: "short",
day: "2-digit",
}).format(new Date(Date.parse(comments.date)))}
</div>
))}
</div>
);
} else {
return <div></div>;
}
}

render() {
if (this.props.campsite) {
return (
<div className="row">
{this.renderCampsite(this.props.campsite)}
{this.renderComments(this.props.comments)}
</div>
);
} else {
return <div></div>;
}
}
}

export default CampsiteInfo;
