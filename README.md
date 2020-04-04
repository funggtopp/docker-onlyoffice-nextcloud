## 集成onlyoffice+mysql+nextcloud的docker安装

文档编辑器使用onlyoffice</br>
数据库使用mysql 8.0


## 基本环境

* Docker (下载或安装指南: [https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/))
* Docker compose (下载或安装指南: [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/))


## 安装

1. 在终端中运行如下命令:

    ```
    git clone https://github.com/funggtopp/docker-onlyoffice-nextcloud-mysql/
    cd docker-onlyoffice-nextcloud-mysql
    ```

2. 运行 Docker Compose:

   
    ```
    sudo docker-compose up -d
    ```

    **注意**:下载各个镜像需要等待一定的时间；如果使用的是阿里云的分镜像可能速度会快一些。例如使用[阿里云杭州站](https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors)

3. 打开浏览器，输入 http://127.0.0.1:80 进入配置页面。在数据库使用选项上，我们应该选择mysql。填空内容请按照我们预设的内容进行填写。
   用户名:nextcloud
   密码:nextcloud123
   数据库名:nextcloud
   主机:db
   －－－－－－－－－
   进入用户主界面后，不要进行任何操作，执行第4步。
   如果对默认的设置进行个性设置，那么在yml文件中，对以下内容进行相应设置即可。将用户名或密码进行变更。
   ```
       environment:
      MYSQL_ROOT_PASSWORD: root123456
      MYSQL_DATABASE: nextcloud
      MYSQL_USER: nextcloud
      MYSQL_PASSWORD: nextcloud123
   ```

4. 运行 `set_configuration.sh` 脚本:

   
    ```
    sudo bash set_configuration.sh
    ```

  脚本将自动安装onlyoffice连接器，并对其进行相应设置。需要注意的是，一般情况下，在国内环境是无法正常自动安装的。如果有显示onlyoffice 无法正确安装，此时，需要进行手动安装。
  ### 手动安装onlyoffice app
  *(1)从https://apps.nextcloud.com/ 下载到onlyoffice的压缩包。
  *(2)解压。（要按目录结构解压才行)
  *(3)将onlyoffice目录完整拷贝到项目目录的app_data/apps目录下。
  *(4)进入nextcloud设置页面。在应用选项卡里能看到onlyoffice了。
  *(5)手动设置。将'Document Editing Service address'设置为'/ds-vpath/'；将'Document Editing Service address for internal requests from the server'设置为'http://onlyoffice-document-server/' ；将'Server address for internal requests from the Document Editing Service'设置为'http://nginx-server/'
  *(6)保存。


## ONLYOFFICE Document Server editions

 Here we offer you to deploy ownCloud with preconfigured free version of ONLYOFFICE Document Server. Note that there're commercial versions of it. 

**ONLYOFFICE Document Server:**

* Community Edition (`onlyoffice-documentserver` package)

* Integration Edition (`onlyoffice-documentserver-ie` package)

The table below will help you make the right choice.

| Pricing and licensing | Community Edition | Integration Edition |
| ------------- | ------------- | ------------- |
| | [Get it now](https://www.onlyoffice.com/download.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)  | [Start Free Trial](https://www.onlyoffice.com/connectors-request.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)  |
| Cost  | FREE  | [Go to the pricing page](https://www.onlyoffice.com/integration-edition-prices.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)  |
| Simultaneous connections | up to 20 maximum  | As in chosen pricing plan |
| Number of users | up to 20 recommended | As in chosen pricing plan |
| License | GNU AGPL v.3 | Proprietary |
| **Support** | **Community Edition** | **Integration Edition** | 
| Documentation | [Help Center](https://helpcenter.onlyoffice.com/server/docker/opensource/index.aspx) | [Help Center](https://helpcenter.onlyoffice.com/server/integration-edition/index.aspx) |
| Standard support | [GitHub](https://github.com/ONLYOFFICE/DocumentServer/issues) or paid | One year support included |
| Premium support | [Buy Now](https://www.onlyoffice.com/support.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC) | [Buy Now](https://www.onlyoffice.com/support.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC) |
| **Services** | **Community Edition** | **Integration Edition** |
| Conversion Service                | + | + |
| Document Builder Service          | + | + |
| **Interface** | **Community Edition** | **Integration Edition** |
| Tabbed interface                       | + | + |
| White Label                            | - | - |
| Integrated test example (node.js)*     | - | + |
| Mobile web editors | - | + |
| **Plugins & Macros** | **Community Edition** | **Integration Edition** |
| Plugins                           | + | + |
| Macros                            | + | + |
| **Collaborative capabilities** | **Community Edition** | **Integration Edition** |
| Two co-editing modes              | + | + |
| Comments                          | + | + |
| Built-in chat                     | + | + |
| Review and tracking changes       | + | + |
| Display modes of tracking changes | + | + |
| Version history                   | + | + |
| **Document Editor features** | **Community Edition** | **Integration Edition** |
| Font and paragraph formatting   | + | + |
| Object insertion                | + | + |
| Adding Content control          | - | + | 
| Editing Content control         | + | + | 
| Layout tools                    | + | + |
| Table of contents               | + | + |
| Navigation panel                | + | + |
| Mail Merge                      | + | + |
| Comparing Documents             | - | +* |
| **Spreadsheet Editor features** | **Community Edition** | **Integration Edition** |
| Font and paragraph formatting   | + | + |
| Object insertion                | + | + |
| Functions, formulas, equations  | + | + |
| Table templates                 | + | + |
| Pivot tables                    | +** | +** |
| **Presentation Editor features** | **Community Edition** | **Integration Edition** |
| Font and paragraph formatting   | + | + |
| Object insertion                | + | + |
| Animations                      | + | + |
| Presenter mode                  | + | + |
| Notes                           | + | + |
| | [Get it now](https://www.onlyoffice.com/download.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)  | [Start Free Trial](https://www.onlyoffice.com/connectors-request.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)  |

\*  It's possible to add documents for comparison from your local drive, from URL and from Nextcloud storage.

\** Changing style and deleting (Full support coming soon)


## Project Information

Official website: [https://www.onlyoffice.com/](https://www.onlyoffice.com/?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)

Code repository: [https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud](https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud "https://github.com/ONLYOFFICE/docker-onlyoffice-nextcloud")

Integration Edition: [http://www.onlyoffice.com/connectors-nextcloud.aspx](https://www.onlyoffice.com/connectors-nextcloud.aspx?utm_source=github&utm_medium=cpc&utm_campaign=GitHubDockerNC)


## User Feedback and Support

If you have any problems with or questions about [ONLYOFFICE Document Server][2], please visit our official forum to find answers to your questions: [dev.onlyoffice.org][1] or you can ask and answer ONLYOFFICE development questions on [Stack Overflow][3].

[1]: http://dev.onlyoffice.org
[2]: https://github.com/ONLYOFFICE/DocumentServer
[3]: http://stackoverflow.com/questions/tagged/onlyoffice
