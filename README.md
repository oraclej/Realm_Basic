# Realm_Basic

Applying Security Realm on Java EE Web Application
using the following tools:
- Jakarta 9
- Apache Tomcat 10
- JDK 17

Some Changes in Tomcat like:

###UserDatabaseRealm

#### $CATALINA_HOME/conf/tomcat-users.xml

><code>&lt;role rolename="admin"/><br>
&lt;role rolename="user"/><br>
&lt;user username="admin" password="123" roles="admin"/><br>
&lt;user username="user" password="123" roles="user"/><br>
</code>
###DataSourceRealm
#### $CATALINA_HOME/conf/context.xml
><code><Resource name="jdbc/oralocalDB"
auth="Container"
type="javax.sql.DataSource"
username="c##arash"
password="123"
driverClassName="oracle.jdbc.driver.OracleDriver"
url="jdbc:oracle:thin:@localhost:1521:XE"
maxTotal="5"
maxIdle="3"
/></code>

#### $CATALINA_HOME/conf/server.xml

><code><Realm  className="org.apache.catalina.realm.DataSourceRealm"
localDataSource="true"
userTable="USERS"
userNameCol="USERNAME"
userCredCol="PASSWORD"
userRoleTable="ROLES"
roleNameCol="ROLE_NAME"
dataSourceName="jdbc/oralocalDB"/>
> </code>

> [!IMPORTANT]
> Dont forget to copy JDBC Driver Library to the Tomcat Lib folder