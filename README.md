# Maven là gì?

Maven về cơ bản là một công cụ để quản lý dự án về:
* Xây dựng (builds)
* Tài liệu hóa (documentation)
* Báo cáo (Reporting)
* Dependencies
* SCMS
* Phát hành (Releases)
* Phân phối (Distribution)

# Maven tạo thuận lợi trong quá trình phát triển như thế nào?

Maven cung cấp lợi ích cho xây dựng quy trình bằng cách sử dụng các chuẩn conventions và practices để thúc đẩy chu kỳ phát triển của bạn đồng thời giúp bạn đạt được một tỷ lệ thành công cao hơn.

# Creating the first Maven project?

Để tạo Maven project đầu tiên, chúng ta sử dụng cơ chế ```archetype``` của Maven. Trong Maven, một archetype là một template của một project được kết hợp với một vài đầu vào của người dùng để đưa ra một Maven project.

Sau đây để tạo một Maven project đơn giản chung ta thực hiện lệnh sau:

```
mvn -B archetype:generate \
  -DarchetypeGroupId=org.apache.maven.archetypes \
  -DgroupId=com.mycompany.app \
  -DartifactId=my-app
```

Khi thực hiện lên trên xong ta sẽ có một project với tên là ```my-app```, trong project này có chứa một file là ```pom.xml``` như sau:

```
<project xmlns="http://maven.apache.org/POM/4.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                      http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.mycompany.app</groupId>
  <artifactId>my-app</artifactId>
  <packaging>jar</packaging>
  <version>1.0-SNAPSHOT</version>
  <name>Maven Quick Start Archetype</name>
  <url>http://maven.apache.org</url>
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

```pom.xml``` chứa Project Object Model cho project. POM là đơn vị làm việc cơ bản trong Maven. Nói đơn giản POM chứa tất cả các thông tin quan trọng về dự án của bạn.

Trong file ```pom.xml``` chúng ta cần phải nắm được các keyword sau:

* **project**: Là element cao nhất trong các file ```pom.xml```
* **modelVersion**: Element này cho biết rằng phiên bản của object model mà POM đang sử dụng. Phiên bản của model ít khi thay đổi nhưng bắt buộc phải có để đảm bảo tính ổn định sử dụng khi developers cần thay đổi model.
* **groupId**: Element này dùng để định danh duy nhất của tổ chức/nhóm tạo ra project. ```groupId``` là một trong định danh chính của một project thông thường dựa trên tên miền của công ty/tổ chức của bạn. Ví dụ: ```org.apache.maven.plugins``` là ```groupId``` cho các Maven plugins.
* **artifactId**: Element này là tên cơ sở duy nhất của Primary ```artifact``` sẽ được generated bởi project. ```Primary artifact``` cho project file ```pom.xml``` này có extension là ```.JAR```. Một ```artifact``` được xuất bản bởi Maven có dạng: ```<artifactId>-<version>.<extension>```. Ví dụ ```myapp-1.0.jar```
* **packaging**: Element này chỉ đỉnh loại đóng gói được sử dụng của ```artifact``` (JAR, WAR, EAR, etc.). Ngoài ra cũng dùng biểu diễn một lifecycle cụ thể dùng trong quá trình build.
* **version**: Elemen này chỉ định version của ```artifact``` được sinh ra bởi project. Maven giúp bản quản lý version, bạn thường thấy phiên bản là ```SNAPSHOT```, đây là trạng thái development.
* **name**: Element này chỉ định tên của project. Được dùng để sinh Maven document.
* **url**: Element này chỉ định nơi mà project có được tìm thấy. Được dùng để sinh Maven document.
* **description**: Element này cung cấp mô tả về project của bạn. Được dùng để sinh Maven document.

Cấu trúc của project trên như sau:

```
my-app
|-- pom.xml
`-- src
    |-- main
    |   `-- java
    |       `-- com
    |           `-- mycompany
    |               `-- app
    |                   `-- App.java
    `-- test
        `-- java
            `-- com
                `-- mycompany
                    `-- app
                        `-- AppTest.java
```

Như bạn có thể thấy rằng, project được tạo từ archetype có một file POM, một source tree cho application và một source tree cho test. Đây là bố cụ chuẩn cho các project Maven (```application sources``` bắt đầu từ ```${basedir}/src/main/java``` và ```test sources``` bắt đầu từ ```${basedir}/src/test/java```, trong đó ```${basedir}``` đại diện cho thư mục chứa ```pom.xml```)
