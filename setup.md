# 環境を作っていく手順

## 最初にやること

### 1. yarn add

```bash
# redux
yarn add @reduxjs/toolkit react-redux
# emotion
yarn add @emotion/native @emotion/react
# react-navigate
yarn add @react-navigation/native
yarn add @react-navigation/native-stack
expo install react-native-screens react-native-safe-area-context
yarn add react-native-gesture-handler
yarn add react-native-elements
  # expo installを使うと今の環境に合わせて良い感じにinstallしてくれる
  # https://reactnavigation.org/docs/5.x/getting-started/
# eslint
yarn add -D eslint
```

### 2. 必要なファイルの作成

```json:.prettierrc
{
  "trailingComma": "es5",
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```

`npx eslint --init`でファイルを作成することになる

```bash
$ npx eslint --init
√ How would you like to use ESLint? · style
√ What type of modules does your project use? · esm
√ Which framework does your project use? · react
√ Does your project use TypeScript? · No / Yes
√ Where does your code run? · node
√ How would you like to define a style for your project? · guide
√ Which style guide do you want to follow? · airbnb
√ What format do you want your config file to be in? · JSON
```

```json:.eslintrc.json(ref)
{
  "env": {
    "browser": true,
    "es2021": true
  },
  "extends": ["plugin:react/recommended", "airbnb"],
  "parserOptions": {
    "ecmaFeatures": {
      "jsx": true
    },
    "ecmaVersion": 12,
    "sourceType": "module"
  },
  "plugins": ["react"],
  "rules": {
    "no-use-before-define": 0,
    "react/no-unstable-nested-components": 0,
    "import/prefer-default-export": 0,
    "react/prop-types": ["error", { "ignore": ["navigation"] }],
    "comma-dangle": "off"
  }
}


```

#### フォルダ構成を作り上げる

```md
- src
  - components
    - .gitkeep
  - screens
    - .gitkeep
  - utils
    - .gitkeep
```

のようにファイルとフォルダを作成しておいて、構成を保って git に push する。

```bash
git status -u
```

### 3. 動作の確認

```bash
# Androidのエミュレータ起動
emulator -list-avds
emulator @Pixel_3_API_29
# 必要に応じて以下のオプションを設定する必要あり
emulator @Pixel_3_API_29a -dns-server 8.8.8.8

```

### 4. expo プロジェクトを開発者間で共有（公開）する

```bash
expo whoami
expo login
expo publish
```

この際に、`app.json`には`"privacy": "unlisted"`を設定する。
