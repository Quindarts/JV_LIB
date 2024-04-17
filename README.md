# JV_LIB

# Setup POM.XML
		<dependencies>
				<!-- https://mvnrepository.com/artifact/org.hibernate.orm/hibernate-core -->
				<dependency>
					<groupId>org.hibernate.orm</groupId>
					<artifactId>hibernate-core</artifactId>
					<version>6.4.1.Final</version>
				</dependency>
				<!--
				https://mvnrepository.com/artifact/com.microsoft.sqlserver/mssql-jdbc -->
				<dependency>
					<groupId>com.microsoft.sqlserver</groupId>
					<artifactId>mssql-jdbc</artifactId>
					<version>12.3.0.jre17-preview</version>
				</dependency>

				    <dependency>
					<groupId>org.junit.jupiter</groupId>
							<artifactId>junit-jupiter-api</artifactId>
							<version>5.10.2</version>
							<scope>test</scope>
					</dependency>
					<dependency>
							<groupId>org.junit.jupiter</groupId>
							<artifactId>junit-jupiter-engine</artifactId>
							<version>5.10.2</version>
							<scope>test</scope>
						</dependency>

		</dependencies>

# Setup Persistence.xml
	<properties>
			<property name="jakarta.persistence.jdbc.driver"
				value="com.microsoft.sqlserver.jdbc.SQLServerDriver" />
			<property name="jakarta.persistence.jdbc.dialect"
				value="org.hibernate.dialect.SQLServerDialect" />
			<property name="hibernate.connection.url"
				value="jdbc:sqlserver://localhost:1433;databaseName=schooldb;trustServerCertificate=true;encrypt=true;" />
			<property name="hibernate.connection.username" value="sa" />
			<property name="hibernate.connection.password"
				value="sapassword" />
			<property name="hibernate.hbm2ddl.auto" value="update" />
			<property name="hibernate.show_sql" value="true" />
			<property name="hibernate.format_sql" value="true" />
		</properties>



# Extend ~ Abstract Class

	3 Type :
 1) Per_class
    			`@Inheritance(strategy = InheritanceType.TABLE_PER_CLASS)`
 	
2) Single_table:
<br/>  <br/>
   	CLASS PERSON:`
			@Entity
			@Table(name = "Person")
			@Inheritance(strategy = InheritanceType.SINGLE_TABLE)
			@DiscriminatorColumn(name = "Discriminator", discriminatorType = DiscriminatorType.STRING)
   `
   <br/>  <br/>  <br/>
	CLASS STUDENT`
			@Entity
			@Table(name = "Student")
			@DiscriminatorValue("Student")
   `
      <br/>  <br/>  <br/>
   	CLASS INSTRUCTOR
   `
   			@Entity
			@Table(name = "Instructor")
			@DiscriminatorValue("Instructor")
`

   <br/>  <br/>


# Server - RMI

	
public class Server {
	private static final String URL = "rmi://H92M17:7878/";
	private static final String URL2 = "rmi://DESKTOP-CVG78RE:7878/";

	public static void main(String[] args) {
		try {
			Context context = new InitialContext();

			CourseDAO courseDAO = new CourseImpl(); // Java Remote object
			StudentDAO studentDAO = new StudentImpl(); // Java Remote object
			DepartmentDAO departmentDAO = new DepartmentImpl(); // Java Remote object

			LocateRegistry.createRegistry(7878);
			context.bind(URL2 + "departmentDAO", departmentDAO);
			context.bind(URL2 + "courseDAO", courseDAO);
			context.bind(URL2 + "studentDAO", studentDAO);

			studentDAO.findStudentsEnrolledInYear(2024);

//			departmentDAO.findDepartmentNotOwnerCourse().forEach((d) -> {
//				System.out.println(d);
//			});
			studentDAO.findStudentsEnrolledInCourse("Calculus").forEach(st -> {
				System.out.println(st);
			});

			System.out.println("Server is running...");
		} catch (Exception e) {
			e.printStackTrace();
		}

	}
}

  # Client - RMI

  public class Client {
	
	private static final String URL = "rmi://H92M17:7878/";
	private static final String URL2 = "rmi://DESKTOP-CVG78RE:7878/";

	public static void main(String[] args) {
		try {
			CourseDAO courseDAO = (CourseDAO) Naming.lookup(URL2 + "courseDAO");
			StudentDAO studentDAO = (StudentDAO) Naming.lookup(URL2 + "studentDAO");
			DepartmentDAO departmentDAO = (DepartmentDAO) Naming.lookup(URL2 + "departmentDAO");
			
			
			studentDAO.findAll().forEach(System.out::println);
			departmentDAO.findDepartmentNotOwnerCourse().forEach(System.out::println);
			
		}catch (Exception e) {
			e.printStackTrace();
		}
		
	}
}


  # GSON
  
  <!--
private static final Gson GSON = new GsonBuilder().create();

	public static Driver getDriver() {
		return GraphDatabase.driver("neo4j://localhost:7687", AuthTokens.basic("neo4j", "12345678"));
	}

	public static <T> T nodeToPOPJO(Node node, Class<T> clazz) {
		Map<String, Object> map = node.asMap();
		String json = GSON.toJson(map);
		T obj = GSON.fromJson(json, clazz);
		return obj;

	};

	public static <T> Map<String, Object> getProp(T t) {
		String json = GSON.toJson(t);
		Map<String, Object> map = GSON.fromJson(json, new TypeToken<Map<String, Object>>() {
		});
		return map;
	}

-->
<!-- https://mvnrepository.com/artifact/com.google.code.gson/gson -->
		<dependency>
			<groupId>com.google.code.gson</groupId>
			<artifactId>gson</artifactId>
			<version>2.10.1</version>
		</dependency>
		<!--
		https://mvnrepository.com/artifact/org.neo4j.driver/neo4j-java-driver -->
		<dependency>
			<groupId>org.neo4j.driver</groupId>
			<artifactId>neo4j-java-driver</artifactId>
			<version>5.18.0</version>
		</dependency>
		<!--
		https://mvnrepository.com/artifact/org.junit.jupiter/junit-jupiter-api -->
		<dependency>
			<groupId>org.junit.jupiter</groupId>
			<artifactId>junit-jupiter-api</artifactId>
			<version>5.10.2</version>
			<scope>test</scope>
		</dependency>

