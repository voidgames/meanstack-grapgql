# MEAN-Stack-GraphQL

# リポジトリ
* githubでこのリポジトリを作った。[meanstack-grapgql]
* フロント、バック両方同じリポジトリに入れる。
* ローカル、~/git で git clone

# バックエンドAPI
* /backend 配下で バックエンドAPIを作る。
* 使用するツール
    * [Express](https://expressjs.com/ja/): 簡単にAPIを作れるjsフレームワーク。
    * [Babel](https://babeljs.io/): 次世代JSの標準機能を、それらの機能をサポートしていないブラウザでも動くコードに変換（トランスパイル）する。
        * __【注意】__ babel v7 では node_module の名前が @babel/~ に変わっている。
        * babel-watch は資材の変更を検知し、自動でビルドし直してくれる。
    * [Apollo](https://www.apollographql.com/): GraphQLのフロントエンド＆バックエンドのライブラリ。今回の主役。
        * __【注意】__ TypeError: graphalExpress is not a function とか出る。
            *  これは、[Apollo v1 -> v2](https://dev.to/gloriamaris/apollo-server-express-10-to-20-fix-graphiqlexpress-and-graphiqlexpress-is-not-a-function-in-a-tutorial-by-xoor-41jn) で、bodyParser, graphqlExpress, graphiqlExpress が消え、ApolloServer に取り替えられたため。
        * ApolloServer は、schema と resolvers を引数に取る。
            * schema は、GraphQLを介して読み書きする全データのtype定義である。必須かつ最上位レベルの type Query から始まり、その下にフィールドがネストされていく構成になっている。
            * schema は graphql(gql) ファイルで定義する。
                * VScodeではGraphQLという拡張を入れておけば、SyntaxHighlightが適用される。
            * Expressのようなミドルウェアを使う場合は、applyMiddleware() でミドルウェアを登録する。