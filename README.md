# Realm_Basic

Applying Security Realm on Java EE Web Application
using the following tools:
- Jakarta 9
- Apache Tomcat 10
- JDK 17

Some Changes in Tomcat like:

### UserDatabaseRealm

#### $CATALINA_HOME/conf/tomcat-users.xml

><code>&lt;role rolename="admin"/><br>
&lt;role rolename="user"/><br>
&lt;user username="admin" password="123" roles="admin"/><br>
&lt;user username="user" password="123" roles="user"/></code>

### DataSourceRealm
#### $CATALINA_HOME/conf/context.xml

><code>&lt;Resource name="jdbc/oralocalDB"<br>
auth="Container"<br>
type="javax.sql.DataSource"<br>
username="c##arash"<br>
password="123"<br>
driverClassName="oracle.jdbc.driver.OracleDriver"<br>
url="jdbc:oracle:thin:@localhost:1521:XE"<br>
maxTotal="5"<br>
maxIdle="3"/></code>

#### $CATALINA_HOME/conf/server.xml

><code>&lt;Realm  className="org.apache.catalina.realm.DataSourceRealm"<br>
localDataSource="true"<br>
userTable="USERS"<br>
userNameCol="USERNAME"<br>
userCredCol="PASSWORD"<br>
userRoleTable="ROLES"<br>
roleNameCol="ROLE_NAME"<br>
dataSourceName="jdbc/oralocalDB"/></code>

> [!IMPORTANT]
> Dont forget to copy JDBC Driver Library to the Tomcat Lib folder