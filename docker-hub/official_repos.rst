.. -*- coding: utf-8 -*-
.. URL: https://docs.docker.com/docker-hub/official_repos/
.. SOURCE: -
   doc version: 1.10
.. check date: 2016/03/11
.. -------------------------------------------------------------------

.. Official Repositories on Docker Hub

.. _official-repositories-on-docker-hub:

========================================
Docker Hub 上の公式リポジトリ
========================================

.. The Docker [Official Repositories](https://hub.docker.com/official/) are a
   curated set of Docker repositories that are promoted on Docker Hub. They are
   designed to:

Docker の `公式リポジトリ <https://hub.docker.com/official/>`_ は Docker Hub 上において提供される、厳選された Docker リポジトリです。
これは以下のことを意識して提供されています。

.. * Provide essential base OS repositories (for example,
     [ubuntu](https://hub.docker.com/_/ubuntu/),
     [centos](https://hub.docker.com/_/centos/)) that serve as the
     starting point for the majority of users.

* 基本的なベース OS となるリポジトリを提供します。
  （たとえば `ubuntu <https://hub.docker.com/_/ubuntu/>`_ , `centos <https://hub.docker.com/_/centos/>`_ などのように）数多くのユーザにとってスタート地点となるものです。

.. * Provide drop-in solutions for popular programming language runtimes, data
     stores, and other services, similar to what a Platform-as-a-Service (PAAS)
     would offer.

* 代表的なプログラミング言語環境、データストア、各種サービスといった、PAAS（Platform-as-a-Service）が提供するものにも似た、一時的な実現環境を提供します。

.. * Exemplify [`Dockerfile` best practices](/engine/userguide/eng-image/dockerfile_best-practices/)
     and provide clear documentation to serve as a reference for other `Dockerfile`
     authors.

* ``Dockerfile`` の :doc:`ベスト・プラクティス </engine/userguide/eng-image/dockerfile_best-practices/>`  の例として示し、わかりやすいドキュメントを提供します。
  これによって ``Dockerfile`` を作成する際のリファレンスとなるようにします。

.. * Ensure that security updates are applied in a timely manner. This is
     particularly important as many Official Repositories are some of the most
     popular on Docker Hub.

* 適切なタイミングでセキュリティ・アップデートを適用するようにします。
  これは特に重要なことです。
  Docker Hub 上における公式リポジトリは、人気を得ているものが数多くあるからです。

.. * Provide a channel for software vendors to redistribute up-to-date and
     supported versions of their products. Organization accounts on Docker Hub can
     also serve this purpose, without the careful review or restrictions on what
     can be published.

* ソフトウェア・ベンダに対して、製品の最新版や正規版を配布するチャネルとして提供します。
  Docker Hub における組織（organization）アカウントもこの目的で利用することができます。
  このアカウントを用いるのであれば、公開しようとするものに対して十分な検証がなくても、また制約を設けなくても、気楽に提供できます。

.. Docker, Inc. sponsors a dedicated team that is responsible for reviewing and
   publishing all Official Repositories content. This team works in collaboration
   with upstream software maintainers, security experts, and the broader Docker
   community.

Docker 社としては、公式リポジトリに関わるさまざまな内容に関して、レビューと公開を担当する専門チームを支援しています。
このチームは、ソフトウェア開発元の保守担当、セキュリティ専門家、Docker コミュニティの幅広い方々と共同して作業を進めています。

.. While it is preferable to have upstream software authors maintaining their
   corresponding Official Repositories, this is not a strict requirement. Creating
   and maintaining images for Official Repositories is a public process. It takes
   place openly on GitHub where participation is encouraged. Anyone can provide
   feedback, contribute code, suggest process changes, or even propose a new
   Official Repository.

公式リポジトリの保守は、ソフトウェア開発元の担当者が行うことが好ましいのは言うまでもありません。
しかしこれを厳密に要求することはしていません。
そもそも公式リポジトリを生成して保守していくことは、公開で行われている作業です。
GitHub 上にて公開で行われているため、そこに参加することが大いに推奨されています。
どなたであっても、フィードバック、コード提供、プロセス変更の提案、さらには新たな公式リポジトリの提案までもが提供できるわけです。


.. ## Should I use Official Repositories?

.. _should-i-use-official-repositories:

公式リポジトリを使うべきですか？
==================================

.. New Docker users are encouraged to use the Official Repositories in their
   projects. These repositories have clear documentation, promote best practices,
   and are designed for the most common use cases. Advanced users are encouraged to
   review the Official Repositories as part of their `Dockerfile` learning process.

Docker を初めて利用するユーザは、公式リポジトリを用いてプロジェクトを構築することをお勧めしています。
このリポジトリには分かり易いドキュメントがあって、ベストプラクティスを示しています。
そして一般的な利用を前提にして設計されています。
上級者の方は ``Dockerfile`` を勉強する一環として、公式リポジトリをレビューしていただくことをお願いします。

.. A common rationale for diverging from Official Repositories is to optimize for
   image size. For instance, many of the programming language stack images contain
   a complete build toolchain to support installation of modules that depend on
   optimized code. An advanced user could build a custom image with just the
   necessary pre-compiled libraries to save space.

公式リポジトリを取得した後に目指すことは、イメージサイズの最適化です。
たとえばプログラミング言語イメージには、たいていは完全なビルドツールチェーンが含まれていて、最適化コードによるモジュールをインストールできるようにしています。
上級者は独自のイメージをビルドする際には、プリコンパイル済ライブラリを必要な分のみ含めることで、容量を節約することができるかもしれません。

.. A number of language stacks such as
   [python](https://hub.docker.com/_/python/) and
   [ruby](https://hub.docker.com/_/ruby/) have `-slim` tag variants
   designed to fill the need for optimization. Even when these "slim" variants are
   insufficient, it is still recommended to inherit from an Official Repository
   base OS image to leverage the ongoing maintenance work, rather than duplicating
   these efforts.

`python <https://hub.docker.com/_/python/>`_ や `ruby <https://hub.docker.com/_/ruby/>`_ のような数多くのプログラミング言語環境向けには ``-slim`` というタグをつけています。
これは最適化への要求を満たす目的で作られています。
この「slim」でも不十分に感じる方は、公式リポジトリ内のベース OS イメージから派生イメージを作り上げて、その後も保守を行っていただくことをお勧めします。
同じやり方を繰り返しても無駄かもしれないからです。

.. ## How do I know the Official Repositories are secure?

.. _how-do-i-know-the-official-repositories-are-secure:

公式リポジトリの安全性はどうすればわかりますか？
=======================================================

.. Docker provides a preview version of Docker Cloud's
   [Security Scanning service](/docker-cloud/builds/image-scan/) for all of the
   Official Repositories located on Docker Hub. These security scan results provide
   valuable information about which images contain security vulnerabilities, which
   you should use to help you choose secure components for your own projects.

Docker Hub 上の公式リポジトリに対しては、Docker Cloud の :doc:`セキュリティ・スキャニング・サービス </docker-cloud/builds/image-scan/>` プレビュー版が提供されます。
このセキュリティ・スキャンから重要な情報が得られます。
つまり、どのイメージにセキュリティぜい弱性が含まれるか、プロジェクトにとって利用すべきセキュアなコンポーネントにはどのようなものがあるかを知らせてくれます。

.. To view the Docker Security Scanning results:

Docker セキュリティ・スキャニングの結果を見るには、以下を行います。

.. 1. Make sure you're logged in to Docker Hub.
       You can view Official Images even while logged out, however the scan results are only available once you log in.
   2. Navigate to the official repository whose security scan you want to view.
   3. Click the `Tags` tab to see a list of tags and their security scan summaries.
       ![](images/scan-drilldown.gif)

1. Docker Hub にログインできていることを確認します。
   公式イメージはログアウトしていても見ることができます。
   しかしスキャン結果を見るためにはログインしている必要があります。
2. セキュリティ・スキャン結果を見たい公式リポジトリを表示します。
3. タブ ``Tags`` をクリックします。
   タグの一覧とともにセキュリティ・スキャンの概要をみることができます。

   ..  ![](images/scan-drilldown.gif)
   .. image:: images/scan-drilldown.gif
      :width: 60%

.. You can click into a tag's detail page to see more information about which
   layers in the image and which components within the layer are vulnerable.
   Details including a link to the official CVE report for the vulnerability appear
   when you click an individual vulnerable component.

タグの詳細ページにクリック移動すれば、イメージ内のどのレイヤに、あるいはレイヤ内のどのコンポーネントにぜい弱性があるかの詳細情報を見ることができます。
個々のぜい弱なコンポーネントをクリックすると、ぜい弱性に関する詳細が表示され、公式の CVE 報告へのリンクが示されます。

.. ## How can I get involved?

.. _how-can-i-get-involved:

どうやったら参加できますか？
=============================

.. All Official Repositories contain a **User Feedback** section in their
   documentation which covers the details for that specific repository. In most
   cases, the GitHub repository which contains the Dockerfiles for an Official
   Repository also has an active issue tracker. General feedback and support
   questions should be directed to `#docker-library` on Freenode IRC.

すべての公式リポジトリのページにはドキュメントが含まれていて、そのリポジトリに対する詳細が説明されています。
そしてその中に **User Feedback** の節があります。
たいていの場合 GitHub リポジトリには、公式リポジトリに対する Dockerfile が含まれており、さらに有効な issue トラッカーも提供されています。
一般的なフィードバックやサポートに関する質問は、Freenode IRC 上の ``#docker-library`` に対して行ってください。

.. ## How do I create a new Official Repository?

.. how-do-i-create-a-new-official-repository:

どうすれば公式リポジトリを生成できますか？
==================================================

.. From a high level, an Official Repository starts out as a proposal in the form
   of a set of GitHub pull requests. You'll find detailed and objective proposal
   requirements in the following GitHub repositories:

高度なレベルで話をすると、公式リポジトリは、GitHub のプルリクエストという形での提案から始まります。
詳細な具体的な提案のあり方については、以下の GitHub リポジトリに示されています。

.. * [docker-library/official-images](https://github.com/docker-library/official-images)

   * [docker-library/docs](https://github.com/docker-library/docs)

* `docker-library/official-images <https://github.com/docker-library/official-images>`_

* `docker-library/docs <https://github.com/docker-library/docs>`_

.. The Official Repositories team, with help from community contributors, formally
   review each proposal and provide feedback to the author. This initial review
   process may require a bit of back and forth before the proposal is accepted.

公式リポジトリ・チームは、コミュニティに貢献して頂ける方の助けも借りながら、正式に各提案をレビューし、提案者へのフィードバックを行っています。
ただし提案を受け付けてからレビューを開始するまでには、多少もたつくことがあるかもしれません。

.. There are also subjective considerations during the review process. These
   subjective concerns boil down to the basic question: "is this image generally
   useful?" For example, the [python](https://hub.docker.com/_/python/)
   Official Repository is "generally useful" to the large Python developer
   community, whereas an obscure text adventure game written in Python last week is
   not.

レビューを行っていく際には、主観的な議論となることもあります。
そのような主観的な疑問は、「このイメージは汎用的に使えますか？」といった単純な質問に帰着します。
たとえば `python <https://hub.docker.com/_/python/>`_ の公式リポジトリは、幅広い Python 開発コミュニティにとって「汎用的に使えます」と言えます。
ところが「先週作った Python のアドベンチャーゲーム」といったあいまいな文章では、何も答えられません。

.. Once a new proposal is accepted, the author is responsible for keeping
   their images up-to-date and responding to user feedback. The Official
   Repositories team becomes responsible for publishing the images and
   documentation on Docker Hub. Updates to the Official Repository follow the same
   pull request process, though with less review. The Official Repositories team
   ultimately acts as a gatekeeper for all changes, which helps mitigate the risk
   of quality and security issues from being introduced.

新たな提案が受け付けられたら、その提案者はイメージを常に最新状態とし、ユーザ・フィードバックに返信する責任があります。
公式リポジトリ・チームには、Docker Hub 上にイメージとドキュメントを公開する義務が発生します。
公式リポジトリを更新していくことは、レビューを行うことは少ないかもしれませんが、プルリクエストの作業に似ています。
公式リポジトリ・チームは、あらゆる活動を最大限管理し、品質リスクやセキュリティ問題の発生を抑えます。


.. seealso:: 

   Official Repositories on Docker Hub
      https://docs.docker.com/docker-hub/official_repos/
