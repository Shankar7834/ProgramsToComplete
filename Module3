using System;
using System.Collections.Generic;

namespace EmployeeIndexerApp
{
    public class Employee
    {
        // Private fields
        private string eid;
        private string fname;
        private int age;

        // Constructor
        public Employee(string eid, string fname, int age)
        {
            this.eid = eid;
            this.fname = fname;
            this.age = age;
        }

        // Indexer to access eid, fname, and age
        public string this[string property]
        {
            get
            {
                return property.ToLower() switch
                {
                    "eid" => eid,
                    "fname" => fname,
                    "age" => age.ToString(),  // Read-only access to age
                    _ => throw new ArgumentException("Invalid property name")
                };
            }
            set
            {
                if (property.ToLower() == "eid")
                {
                    eid = value; // Allow writing to eid
                }
                else if (property.ToLower() == "fname")
                {
                    fname = value; // Allow writing to fname
                }
                else
                {
                    throw new ArgumentException("Only eid and fname are writable.");
                }
            }
        }

        // Optionally, add a ToString method for better display
        public override string ToString()
        {
            return $"EID: {eid}, Name: {fname}, Age: {age}";
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Create a collection of employees using collection initializer
            List<Employee> employees = new List<Employee>
            {
                new Employee("E001", "John", 30),
                new Employee("E002", "Alice", 25),
                new Employee("E003", "Bob", 28)
            };

            // Modify the properties of employees using indexer
            employees[0]["eid"] = "E004";   // Changing eid of first employee
            employees[1]["fname"] = "Alicia"; // Changing fname of second employee

            // Output the modified data
            foreach (var employee in employees)
            {
                Console.WriteLine(employee);
            }

            // Trying to access and modify read-only age (for demonstration)
            try
            {
                employees[0]["age"] = "35"; // This will throw an exception
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);  // "Only eid and fname are writable."
            }

            // Access read-only age (will work)
            Console.WriteLine($"Age of first employee: {employees[0]["age"]}");
        }
    }
}
