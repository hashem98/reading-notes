# Hibernate Many to Many
A many-to-many relationship occurs when multiple records in a table are associated with multiple records in another table. For example, a many-to-many relationship exists between customers and products: customers can purchase various products, and products can be purchased by many customers

![](https://fmhelp.filemaker.com/help/18/fmp/en/FMP_Help/images/relational.07.06.1.png)

1. Database Setup creat tables insert data with it's values
2. next step would be the preparation of the dependencies 
3. create model classes with JPA annotations

 This association has two sides 
 *the owning side* :the join table is specified on the owning side by using the `@JoinTable` annotation,The @JoinTable is used to define the join/link table.

  *the inverse side*:
The @JoinColumn annotation is used to specify the join/linking column with the main table.

 UNIT test
 ```
 public class HibernateManyToManyAnnotationMainIntegrationTest {
    private static SessionFactory sessionFactory;
    private Session session;

    @Test
    public void givenData_whenInsert_thenCreatesMtoMrelationship() {
        String[] employeeData = { "Peter Oven", "Allan Norman" };
        String[] projectData = { "IT Project", "Networking Project" };
        Set<Project> projects = new HashSet<>();

        for (String proj : projectData) {
            projects.add(new Project(proj));
        }

        for (String emp : employeeData) {
            Employee employee = new Employee(emp.split(" ")[0], 
              emp.split(" ")[1]);
 
            assertEquals(0, employee.getProjects().size());
            employee.setProjects(projects);
            session.persist(employee);
 
            assertNotNull(employee);
        }
    }

    @Test
    public void givenSession_whenRead_thenReturnsMtoMdata() {
        @SuppressWarnings("unchecked")
        List<Employee> employeeList = session.createQuery("FROM Employee")
          .list();
 
        assertNotNull(employeeList);
 
        for(Employee employee : employeeList) {
            assertNotNull(employee.getProjects());
        }
    }

    
 }

 ````


# notes from James Mickens in Security
1. should we care more about how to put our data on websites like your email account should be with strong password and for Organized criminals breaking into
your email account and sending
spam using your identity your account should be Strong passwords + common
sense (don’t click on unsolicited
herbal Viagra ads that result in
keyloggers and sorrow)  
2. the security issue should be more carable in our using and we should focuse to not use the same data for each using

