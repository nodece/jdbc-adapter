JDBC Adapter
====

JDBC Adapter is the [JDBC](https://en.wikipedia.org/wiki/Java_Database_Connectivity) adapter for [jCasbin](https://github.com/casbin/jcasbin). With this library, jCasbin can load policy from JDBC supported database or save policy to it.

Based on [Supported JDBC Drivers and Databases](https://docs.oracle.com/cd/E19226-01/820-7688/gawms/index.html), The current supported databases are:

- MySQL
- Java DB
- Oracle
- PostgreSQL
- DB2
- Sybase
- Microsoft SQL Server

## Installation

    git clone https://github.com/jcasbin/jdbc-adapter

## Simple Example

```java
package com.company.test;

import org.casbin.jcasbin.main.Enforcer;
import org.casbin.jcasbin.util.Util;

public class Test {
    public static void main() {
        // Initialize a JDBC adapter and use it in a jCasbin enforcer:
        // The adapter will use the existing MySQL database named "casbin_rule".
        JDBCAdapter a = new JDBCAdapter("com.mysql.cj.jdbc.Driver", "jdbc:mysql://localhost:3306/casbin_rule", "root", "1234"); // Your driver and URL. 

        Enforcer e = new Enforcer("examples/rbac_model.conf", a);

        // Load the policy from DB.
        e.loadPolicy();

        // Check the permission.
        e.enforce("alice", "data1", "read");

        // Modify the policy.
        // e.addPolicy(...);
        // e.removePolicy(...);

        // Save the policy back to DB.
        e.savePolicy();
    }
}
```

## Getting Help

- [jCasbin](https://github.com/casbin/jcasbin)

## License

This project is under Apache 2.0 License. See the [LICENSE](LICENSE) file for the full license text.