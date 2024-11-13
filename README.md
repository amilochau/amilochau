<h1 align="center" style="display: flex; justify-content: center; align-items: center; gap: 16px;">
  <a href="https://milochau.com" target="_blank">
    <img alt="milochau logo" width="100" src="./assets/logo.png">
  </a>
  Antoine Milochau
</h1>

## About me, Antoine Milochau

I'm a Cloud Architect, working on Azure and AWS solutions. I'm particularly using .NET for almost 15 years, and TypeScript for 10 years, then using more and more Cloud-native solutions - focused on serverless, easy-to-use by design. Contact me on LinkedIn to start the discussion!

The `amilochau` account contains projects and repositories with Microsoft & AWS technologies. My first motivation has been to test, with real-life scenarios, multiple languages, frameworks and Cloud resources proposed by Microsoft and AWS. From these investigations, multiple results have been produced.

## Technical solutions

Technical solutions are focused on Cloud-native platform implementation, serverless technologies, fully integrated DevOps workflows, and beautiful UIs. These solutions are proposed in the `amilochau` repositories - packages are public, MIT-licensed, and published in common registries; business use cases are deployed within the [milochau.com](https://milochau.com) domain name, coming mostly from private repositories, in the `milochaucom` organization.

Here are the most important packages, part of my projects:

|   |   |
|---|---|
| [tf-modules](https://github.com/amilochau/tf-modules) | Terraform modules (Infrastructure as Code) to manage AWS & GitHub resources |
| [core-vue3](https://github.com/amilochau/core-vue3) | vue.js v3 plugins to create UI applications with common features |
| [core-aws](https://github.com/amilochau/core-aws) | NuGet packages (.NET 9) as helpers for AWS Lambda-based applications |
| [github-actions](https://github.com/amilochau/github-actions) | Custom GitHub Actions to help build and deploy applications and packages within Azure, AWS, GitHub |
| [azure-templates](https://github.com/amilochau/azure-templates) | Bicep templates (Infrastructure as Code) to deploy Azure resources |

## Business solutions

Here are some business solutions that have been implemented and deployed:

|   |   |
|---|---|
| [maps.milochau.com](https://maps.milochau.com) | Create your own maps with custom makers, lines and layer groups |
| [operations.milochau.com](https://operations.milochau.com) | Create your operations lists, to share validated expenses with your friends or family |
| [contact.milochau.com](https://contact.milochau.com) | Contact me if you want to learn more on my projects |
| [cv.milochau.com](https://cv.milochau.com) | My own Curriculum Vitae |

Technical modules are used behind the scenes, to avoid repetition:

- `emails`: internal technical service to send compliant templatized emails; including unsubscribe list and bounce/complain feedbacks - based mostly on AWS SES, AWS DynamoDB, AWS SNS
- `identity`: identity provider to manage users and groups - based mostly on AWS Cognito
- `permissions`: permissions service to manage Attribute-Based Access Control in business solutions - based mostly on AWS DynamoDB, AWS Cognito
- `trackings`: audit service to track business-related events in business solutions - based mostly on AWS DynamoDB
- `management`: global configuration for AWS Accounts

## Future topics

You can learn more on my work, past and future on these pages:

- The **roadmap** can be found [on this page](./docs/roadmap.md)
- The `amilochau` repositories **top contributors** can be found [on this page](./docs/contributors.md)
