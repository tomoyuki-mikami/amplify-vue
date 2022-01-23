# 手順

## front
```shell
# install amplify cli
npm install -g @aws-amplify/cli
# install vue cli
npm install -g @vue/cli

# create vue project
vue create amplify-vue
?  Your connection to the default yarn registry seems to be slow.
   Use https://registry.npm.taobao.org for faster installation? Yes


Vue CLI v4.5.15
? Please pick a preset: Default (Vue 3) ([Vue 3] babel, eslint)
? Pick the package manager to use when installing dependencies: Yarn
```

http://localhost:8080 確認
```shell
cd amplify-vue
yarn serve
```

## front で使う Amplify プラグインのインストール
```shell
yarn add aws-amplify @aws-amplify/ui-components
```


## Amplify セットアップ
```shell
# amplify 用の aws profile の設定などを行う
#   ~/.aws/ 配下に Amplify を操作できる権限の profile があれば不要
amplify configure

# amplify 構築
amplify init

# 状況確認（特になにもリソースはない）
amplify status
```

## API 追加
```shell
amplify add api
? Select from one of the below mentioned services: REST
✔ Provide a friendly name for your resource to be used as a label for this category in the project: · api5d217c5d
✔ Provide a path (e.g., /book/{isbn}): · /items
Only one option for [Choose a Lambda source]. Selecting [Create a new Lambda function].
? Provide an AWS Lambda function name: getData
? Choose the runtime that you want to use: NodeJS
? Choose the function template that you want to use: Hello World

Available advanced settings:
- Resource access permissions
- Scheduled recurring invocation
- Lambda layers configuration
- Environment variables configuration
- Secret values configuration

? Do you want to configure advanced settings? Yes
? Do you want to access other resources in this project from your Lambda function? No
? Do you want to invoke this function on a recurring schedule? No
? Do you want to enable Lambda layers for this function? No
? Do you want to configure environment variables for this function? No
? Do you want to configure secret values this function can access? No
? Do you want to edit the local lambda function now? No
Successfully added resource getData locally.

Next steps:
Check out sample function code generated in <project-dir>/amplify/backend/function/getData/src
"amplify function build" builds all of your functions currently in the project
"amplify mock function <functionName>" runs your function locally
To access AWS resources outside of this Amplify app, edit the /Users/mika/Development/AmplifyVueSample/amplify/backend/function/getData/custom-policies.json
"amplify push" builds all of your local backend resources and provisions them in the cloud
"amplify publish" builds all of your local backend and front-end resources (if you added hosting category) and provisions them in the cloud
✅ Succesfully added the Lambda function locally
✔ Restrict API access? (Y/n) · yes
✔ Who should have access? · Authenticated and Guest users
✔ What permissions do you want to grant to Authenticated users? · create, read, update, delete
✔ What permissions do you want to grant to Guest users? · read
✅ Successfully added auth resource locally.
✔ Do you want to add another path? (y/N) · no
✅ Successfully added resource api5d217c5d locally

✅ Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
```

## s3 追加
```shell
amplify add storage
? Select from one of the below mentioned services: Content (Images, audio, video, etc.)
✔ Provide a friendly name for your resource that will be used to label this category in the project: · s3198a5392
✔ Provide bucket name: · amplifyvuesample5353e9091fc1497da5eb02c5498cee6
✔ Who should have access: · Auth and guest users
✔ What kind of access do you want for Authenticated users? · create/update, read, delete
✔ What kind of access do you want for Guest users? · read
✔ Do you want to add a Lambda Trigger for your S3 Bucket? (y/N) · no
✅ Successfully added resource s3198a5392 locally

⚠️ If a user is part of a user pool group, run "amplify update storage" to enable IAM group policies for CRUD operations
✅ Some next steps:
"amplify push" builds all of your local backend resources and provisions them in the cloud
"amplify publish" builds all of your local backend and front-end resources (if you added hosting category) and provisions them in the cloud
```

## バックエンドのデプロイ
```shell
# 確認
amplify status
# デプロイ
amplify push
```

## フロントエンドのデプロイ
GitHub などで連携する場合はコンソールから

CLI でやる場合
```shell
amplify add hosting （初回のみ）
amplify publish
```
