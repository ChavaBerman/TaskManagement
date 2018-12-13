# TaskManagement
developed by Tamar Frishman and Chava Berman

## Using this technologies:
* MySql
* Web api
* WinForms
* Angular
* PHP

# DB schema
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/DB.png)

# Test api with postman
### Workers Controller

### GetAllWorkers

![picture]( https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA1.PNG)

### GetAllTeamHeads

![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA2.PNG)

### GetWorkers (such as 'Developers','QA','UIUX')
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA3.PNG)

### GetAllowedWorkers(teamHeadId)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA4.PNG)

### GetWorkersByTeamHead(teamHeadId)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA5.PNG)

### SendMessageToManager
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA6.PNG)

### GetWorkerDetails(teamHeadId)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA7.PNG)

### AddWorker(error response)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA8.PNG)

### AddWorker
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA9.PNG)

### LoginByPassword(error response)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA10.PNG)

### LoginByPassword
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA11.PNG)

### LoginByComputerWorker(error response)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA12.PNG)

### LoginByComputerWorker
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA13.PNG)

### ForgotPassword(emailAdress,userName)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA14.PNG)

### ForgotPassword(error response)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA15.PNG)

### UpdateWorker(idWorker)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA16.PNG)

### RemoveWorker(idWorker)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA17.PNG)

### SetNewPassword
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA18.PNG)

### SetNewPassword(error response)
![picture](https://github.com/ChavaBerman/TaskManagement/blob/master/workersController/%D7%A9%D7%A7%D7%95%D7%A4%D7%99%D7%AA19.PNG)


***
## Web api
### Models
* Worker:
    * WorkerId - int, Key
    * WorkerName - string - MinLength: 2, MaxLength:15, Required,UniqueName
    * Password - string - MinLength: 6, MaxLength:6, RequiredIf, UniquePassword,Regex,DataType
    * ConfirmPassword - string - minLength: 6, maxLength:6,DataType,Compare 
    * Email - string  ,Required, UniqueEmail,EmailAddress
    * WorkerComputer - string - UniqueWorkerComputer
    * NumHoursWork - decimal 
    * ManagerId - int
    * StatusId - int
    * IsNewWorker - bool,DefaultValue(true)
    * IsFollowedByTeamHead - bool,DefaultValue(false)
* Project:
    * ProjectId - int 
    * ProjectName - string -  MinLength: 2, MaxLength:15, Required,UniqueProjectName
    * CustomerName - string -  minLength: 2, maxLength:15, Required,
    * DateBegin - DateTime- Required,ValidDateTimeBegin
    * DateEnd - DateTime - Required,ValidDateTimeBegin
    * IdTeamHead - int 
    * DevHours - decimal - Range(0, int.MaxValue),DefaultValue(0)
    * QAHours - decimal - Range(0, int.MaxValue), DefaultValue(0)
    * UIUXHours - decimal - Range(0, int.MaxValue),DefaultValue(0)
    * tasks - List<Models.Task>
* Task:
    * IdTask - int -Key
    * ReservingHours - decimal-Range(0,int.MaxValue),DefaultValue(0)
    * GivenHours - decimal-Range(0, int.MaxValue),DefaultValue(1)
    * IdWorker - int 
    * IdProject - int
    * projectName - string
    * workerName - string
* PresenDay:
     * IdPresentDay - int-Key
     * TimeBegin - DateTime
     * TimeEnd - DateTime 
    * sumHoursDay - decimal 
    * WorkerId - int 
    * ProjectId - int
    * ReservingHours - decimal - Required,ValidDateTimeBegin
    * Comment - string- DefaultValue("")
    * Description - string - DefaultValue("")
 * Report:
    * Id - int 
    * ParentId - int -  MinLength: 2, MaxLength:15, Required,UniqueProjectName
    * Name - string -  minLength: 2, maxLength:15, Required,
    * TeamHeader - string- Required,ValidDateTimeBegin
    * ReservingHours - decimal - Required,ValidDateTimeBegin
    * GivenHours - decimal 
    * Customer - string - Range(0, int.MaxValue),DefaultValue(0)
    * DateBegin - DateTime - Range(0, int.MaxValue), DefaultValue(0)
    * DateEnd - DateTime - Range(0, int.MaxValue),DefaultValue(0)
    * Days - int
    * WorkedDays -int
 * Status:
     * Id - int-Key
     * StatusName - string

### Controllers
* PresentDay Controller:
    * Post - Add PresentDay instance    
    requierd data: 
       * PresentDay value  
    * Post - UpdatePresentDay
    requierd data: 
        * PresentDay value
    * Post - GetPresentByWorkerId
    requierd data: 
        * WorkerId
        
* Project controller:
    * Get - GetAllProjects   
    returns all the projects
    * Get - GetAllProjectsByTeamHead
    requierd data: 
          * TeamHeadId 
    * Get - GetAllProjectsByWorkerId
    requierd data: 
          * WorkerId
    * Get - GetProjectState
    requierd data: 
          * ProjectId
    * Post - AddProject
    requierd data: 
          * Project instance
          
* Reports controller:
    * Get - GetReportData-gets the data for report vuew
* Status controller:
    * Get - GetAllstatuses-gets all types of statuses.
    
* Task Controller:
    * Post - AddTask    
    requierd data: 
       * Task value  
    * Get - GetTasksWithWorkerAndProjectByProjectId
    requierd data: 
        * projectId
    * Get - GetTasksWithWorkerAndProjectByWorkerId
    requierd data: 
        * WorkerId    
    * Get - GetWorkersDictionary-for viewing charts
    requierd data: 
        * projectId   
    * Put - UpdateTask
    requierd data: 
        * task value 
    * Get - GetWorkerTasksDictionary-for viewing chrtas
    requierd data: 
        * WorkerId 
        
* Workers Controller:
    * Get - GetAllWorkers    
    * Get - GetAllTeamHeads
    * Get - GetWorkers-get workers(DEV-QA-UIUX)   
    * Get - GetAllowedWorkers-get all workers that are not belong to this team head (gets team head id):
    requierd data: 
        * TeamHeadId   
    * Get - GetWorkersByTeamhead
    requierd data: 
        * teamHeadId 
    * Get - GetWorkerDetails
    requierd data: 
        * WorkerId 
    * Post - SendMessage -send email-(gets EmailParams object that contains worker id, subject and message)
    requierd data: 
        * EmailParams value
    * Post - SendMessageToManager -send message to manager-(gets EmailParams object that contains worker id, subject and message)
    requierd data: 
        * EmailParams value
    * Post - AddWorker -send message to manager-(gets EmailParams object that contains worker id, subject and message)
    requierd data: 
        * Worker value 
    * Post - LoginByPassword -login to system with worker name and password (gets LoginWorker object that contains name and password):
    requierd data: 
        * LoginWorker value 
    * Post - LoginByComputerWorker -login by computer (gets ComputerLogin object taht contains ComputerIp):password):
    requierd data: 
        * ComputerLogin value 
    * Get - ForgotPassword :
    requierd data: 
        * email 
        * workerName
    * Put - UpdateWorker :
    requierd data: 
        * worker value 
    * Post
    required date
        * ForgotPassword value
***
# Code of each tier

### DAL
```csharp
using System;
using System.Collections.Generic;
using MySql.Data.MySqlClient;

namespace DAL
{
    public static class DBAccess
    {

        static MySqlConnection Connection = new MySqlConnection("SERVER=127.0.0.1;PORT=3306;UID=root;PASSWORD=1234;persistsecurityinfo=True;DATABASE=task;SslMode = none");

        public static int? RunNonQuery(string query)
        {
            lock (Connection)
            {
                try
                {
                    Connection.Open();
                    MySqlCommand command = new MySqlCommand(query, Connection);
                    return command.ExecuteNonQuery();
                }
                catch (Exception ex)
                {
                    return null;
                }
                finally
                {
                    if (Connection.State != System.Data.ConnectionState.Closed)
                    {
                        Connection.Close();
                    }
                }
            }

        }

        public static object RunScalar(string query)
        {
            lock (Connection)
            {
                try
                {
                    Connection.Open();
                    MySqlCommand command = new MySqlCommand(query, Connection);
                    return command.ExecuteScalar();
                }
                catch (Exception)
                {
                    return null;
                }
                finally
                {
                    if (Connection.State != System.Data.ConnectionState.Closed)
                    {
                        Connection.Close();
                    }
                }
            }

        }

        public static List<T> RunReader<T>(string query, Func<MySqlDataReader, List<T>> func)
        {
            lock (Connection)
            {
                try
                {
                    Connection.Open();
                    MySqlCommand command = new MySqlCommand(query, Connection);
                    MySqlDataReader reader = command.ExecuteReader();
                    return func(reader);
                }
                catch (Exception ex)
                {
                    return null;
                }
                finally
                {
                    if (Connection.State != System.Data.ConnectionState.Closed)
                    {
                        Connection.Close();
                    }
                }
            }

        }

    }
}

```

### BOL
``csahrp

using BOL.Models;
using BOL.Validations;
using System.Collections.Generic;
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;


namespace BOL
{
    public class Worker
    {
        public Worker()
        {
            Projects = new List<Project>();
            PresentsDayWorker = new List<PresentDay>();
            workers = new List<Worker>();
        }
        [Key]
        public int WorkerId { get; set; }
        [UniqueName]
        [Required(ErrorMessage = "name is required")]
        [MinLength(2, ErrorMessage = "name must be more than 2 chars"), MaxLength(15, ErrorMessage = "name must be less than 15 chars")]
        public string WorkerName { get; set; }

        [RequiredIf("IsNewWorker", true,
              ErrorMessageResourceName = "PasswordRequired")]
        [UniquePassword]
        [MinLength(64), MaxLength(64)]
        [RegularExpression(@"[A-Za-z0-9]+", ErrorMessage = "Password can contain only letters and numbers")]
        [DataType(DataType.Password)]
        public string Password { get; set; }
        [DataType(DataType.Password)]
        [Compare("Password", ErrorMessage = "The password and confirmation password do not match")]
        private string confirmPassword { set; get; }
        [Required(ErrorMessage = "email is required")]
        [UniqueEmail]
        [EmailAddress]
        public string Email { get; set; }


        //[MinLength(20),MaxLength(50)]
        [UniqueWorkerComputer]
        public string WorkerComputer { get; set; } = "";
        public decimal NumHoursWork { get; set; } = 9;

        public int? ManagerId { get; set; }
        public int StatusId { get; set; }
        [DefaultValue(true)]
        public bool IsNewWorker { get; set; }
        [DefaultValue(false)]
        public bool IsFollowedByTeamHead { get; set; }

        //------------------------------------------------------------
        public Status statusObj { get; set; }
        public List<Project> Projects { get; set; }
        public Worker Manager { get; set; }
        public List<PresentDay> PresentsDayWorker { get; set; }

        public List<Worker> workers { get; set; }

    }
}


```
```csharp
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;

namespace BOL.Models
{
    public class Task
    {

        public int IdTask { get; set; }

        [Range(0,int.MaxValue, ErrorMessage = "Reserving hours can not be less than 0")]
        [DefaultValue(0)]
        public decimal ReservingHours { get; set; }

        [Range(0, int.MaxValue,ErrorMessage ="Given hours can not be less than 0")]
        [DefaultValue(1)]
        public decimal GivenHours { get; set; }
        public int IdWorker { get; set; }
        public int IdProject { get; set; }


        public string projectName { get; set; }
        public string workerName { get; set; }
    }
}

```
```csharp
using System.ComponentModel.DataAnnotations;

namespace BOL
{
    public  class Status
    {
        [Key]
        public int Id { get; set; }
        public string StatusName { get; set; }
    }
}

```
```csharp
using System;

namespace BOL.Models
{
    public class ReportData
    {
        public int Id { get; set; }
        public int ParentId { get; set; }
        public string Name { get; set; }
        public string TeamHeader { get; set; }
        public decimal ReservingHours { get; set; }
        public decimal GivenHours { get; set; }
        public string Customer { get; set; }
        public DateTime? DateBegin { get; set; }
        public DateTime? DateEnd { get; set; }
        public int? Days { get; set; }
        public int? WorkedDays { get; set; }

        public ReportData() { }
        public ReportData(int id, string name, decimal reservingHours, decimal givenHours, decimal presencePercent, int parentId)
        {
            Id = id;
            Name = name;
            ReservingHours = reservingHours;
            GivenHours = givenHours;
            ParentId = parentId;
        }
        public ReportData(int id, string name, string teamheader, decimal hours,decimal presence,decimal presencePercent, int parentId) : this(id, name,hours, presence, presencePercent, parentId)
        {
            TeamHeader = teamheader;
        }
       
    }
}

```
```csharp

using BOL.Models;
using BOL.Validations;
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;

namespace BOL
{
    public class Project
    {

        public Project()
        {

            //HoursForDepartment = new List<HourForDepartment>();
            PresentsDayWorker = new List<PresentDay>();
            workers = new List<Worker>();
        }
        [Key]
        public int ProjectId { get; set; }

        [Required(ErrorMessage = "Name is required")]
        [MaxLength(15, ErrorMessage = "ProjectName grade than 15 chars"), MinLength(2, ErrorMessage = "ProjectName less than 2 chars")]
        [UniqueProjectName]
        public string ProjectName { get; set; }

        [Required(ErrorMessage = "CustomerName is required")]
        [MaxLength(15, ErrorMessage = "CustomerName grade than 15 chars"), MinLength(2, ErrorMessage = "CustomerName less than 2 chars")]
        public string CustomerName { get; set; }



        [Required(ErrorMessage = "DateBegin is required")]
        [ValidDateTimeBegin]
        public DateTime DateBegin { get; set; }


        [Required(ErrorMessage = "DateEnd is required")]
        [ValidDateTimeEnd]
        public DateTime DateEnd { get; set; }

        public bool IsFinish { get; set; } = false;

        public int IdTeamHead { get; set; }

        [Range(0, int.MaxValue)]
        [DefaultValue(0)]
        public decimal DevHours { get; set; }

        [Range(0, int.MaxValue)]
        [DefaultValue(0)]
        public decimal QAHours { get; set; }

        [Range(0, int.MaxValue)]
        [DefaultValue(0)]
        public decimal UIUXHours { get; set; }
        public List<Models.Task> tasks { get; set; }

        //-------------------------
        public Worker Manager { get; set; }



        public List<PresentDay> PresentsDayWorker { get; set; }

        public List<Worker> workers { get; set; }

    }
}

```
```csharp
using System;
using System.ComponentModel;
using System.ComponentModel.DataAnnotations;

namespace BOL.Models
{
    public class PresentDay
    {
        public PresentDay()
        {
        }

        [Key]
        public int IdPresentDay { get; set; }
       //TODO: [ValidDateTimeBegin]
        public DateTime TimeBegin { get; set; }

       //TODO: [ValidDateTimeEnd]
        public DateTime TimeEnd { get; set; }
        public decimal sumHoursDay { get; set; }

        public int WorkerId { get; set; }

        public int ProjectId { get; set; }
        [DefaultValue("")]
        public string Comment { get; set; }
        [DefaultValue("")]
        public string Description { get; set; }

        //------------------------
        public Worker Worker { get; set; }

        public Project Project { get; set; }


    }
}

```
### BLL
```csharp
using DAL;
using BOL;
using BOL.Convertors;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.Net.Mail;

namespace BLL
{
    public class LogicWorker
    {
        /// <summary>
        /// Get all users which defined as workers such as :'developers','QA' etc.
        /// </summary>
        /// <returns>list of workers</returns>
        public static List<Worker> GetAllWorkers()
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus;";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get all users which defined as workers such as :'developers','QA' etc. with their passwords
        /// </summary>
        /// <returns>list of workers</returns>
        public static List<Worker> GetAllWorkersWithPassword()
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus;";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorkerWithPassword(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get a worker by his teamHead
        /// </summary>
        /// <param name="id">teamHead id to search his workers</param>
        /// <returns>list of this teamHead's workers</returns>
        public static List<Worker> GetWorkersByTeamhead(int teamHeadId)
        {

            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE task.user.managerId={teamHeadId};";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get workers by project id
        /// </summary>
        /// <param name="projectId">id of project</param>
        /// <returns>list of workers who works in this project</returns>
        public static List<Worker> GetWorkersByProjectId(int projectId)
        {
            string query = $"SELECT * FROM task.user JOIN task.TASK on task.user.idUser=task.task.idUser WHERE task.task.idProject={projectId};";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get all workers which are not registered under this teamHead
        /// </summary>
        /// <param name="teamHeadId">the teamHead to get the worker for</param>
        /// <returns>list of workers which match the condition</returns>
        public static List<Worker> GetAllowedWorkers(int teamHeadId)
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE task.status.statusname!='TeamHead' and task.status.statusname!='Manager' and task.user.managerId!={teamHeadId};";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get all users which defined as 'TeamHeaders'
        /// </summary>
        /// <returns>list of teamHeads</returns>
        public static List<Worker> GetAllTeamHeads()
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE task.status.statusname='TeamHead';";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get workers only ('DEV','QA','UIUX')
        /// </summary>
        /// <returns>LIST OF MATCHING WORKERS</returns>
        public static List<Worker> GetWorkers()
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE task.status.statusname!='TeamHead' and task.status.statusname!='Manager';";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        ///Get worker's details by id
        /// </summary>
        /// <param name="workerId">id of worker</param>
        /// <returns>worker instance of mathing worker</returns>
        public static Worker GetWorkerDetails(int workerId)
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON user.IdStatus=status.IdStatus WHERE idUser={workerId}";
            List<Worker> workers = new List<Worker>();
            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> projectsWorker = new List<Worker>();
                while (reader.Read())
                {
                    projectsWorker.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return projectsWorker;
            };
            List<Worker> workersList = DBAccess.RunReader(query, func);
            return workersList.Count > 0 ? workersList[0] as Worker : null;
        }

        /// <summary>
        /// Get worker's details by name and email address
        /// </summary>
        /// <param name="workerName"> worker name</param>
        /// <param name="emailAddress">email address</param>
        /// <returns>worker instance of matching worker</returns>
        public static Worker GetWorkerDetailsByNameAndEmail(string workerName, string emailAddress)
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON user.IdStatus=status.IdStatus WHERE userName='{workerName}' and email='{emailAddress}'";
            List<Worker> workers = new List<Worker>();
            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> projectsWorker = new List<Worker>();
                while (reader.Read())
                {
                    projectsWorker.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return projectsWorker;
            };
            List<Worker> workersList = DBAccess.RunReader(query, func);
            return workersList.Count > 0 ? workersList[0] as Worker : null;
        }

        /// <summary>
        /// Get the manager of app
        /// </summary>
        /// <returns>worker instance of manager</returns>
        public static Worker GetManager()
        {
            string query = "SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE task.status.statusname='Manager';";
            List<Worker> managers = new List<Worker>();
            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> manager = new List<Worker>();
                while (reader.Read())
                {
                    manager.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return manager;
            };
            managers = DBAccess.RunReader(query, func);
            return managers.Count > 0 ? managers[0] as Worker : null;
        }


        public static string ForgotPassword(string workerName, string emailAddress)
        {
            Worker worker = GetWorkerDetailsByNameAndEmail(workerName, emailAddress);
            if (worker != null)
            {
                LogicForgetPassword.AddForgetPasswordRow(worker.WorkerId);
                string IdForgetPassword = LogicForgetPassword.GetIdForgetPassword(worker.WorkerId);
                string message = $"Enter to this link: http://localhost:4200/taskManagement/change-password/{IdForgetPassword}";
                string subject = "password from managemet task:";
                if (sendMessage(worker, message, subject))
                    return null;
                return "did not succeed to send you email.";
            }
            return "These details do not match any information.";
        }

        /// <summary>
        /// Get worker's details by name and password
        /// </summary>
        /// <param name="password">password</param>
        /// <param name="workerName">name</param>
        /// <returns>worker instance</returns>
        public static Worker GetWorkerDetailsByPassword(string password, string workerName)
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON user.IdStatus=status.IdStatus  WHERE password='{password}' and username='{workerName}'";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            List<Worker> workersLogin = DBAccess.RunReader(query, func);
            if (workersLogin != null && workersLogin.Count > 0)
            {

                return workersLogin[0];
            }
            return null;

        }

        /// <summary>
        /// Delete worker
        /// </summary>
        /// <param name="workerId">id of worker</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool RemoveWorker(int workerId)
        {
            string query = $"DELETE FROM task.user WHERE idUser={workerId};";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Update worker details
        /// </summary>
        /// <param name="worker">worker with details for updating</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool UpdateWorker(Worker worker)
        {
            string query = $"UPDATE task.user SET IdStatus={worker.StatusId} ,managerId={worker.ManagerId},totalHours={worker.NumHoursWork},userComputer='{worker.WorkerComputer}',is_followed_by_team_head={worker.IsFollowedByTeamHead}  WHERE idUser={worker.WorkerId} ;";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Update password for worker
        /// </summary>
        /// <param name="worker">worker instance for updating</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool UpdatePassword(Worker worker)
        {
            string query = $"UPDATE task.user SET password='{worker.Password}'  WHERE idUser={worker.WorkerId} ;";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Add worker to DB
        /// </summary>
        /// <param name="worker">worker instance for adding</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool AddWorker(Worker worker)
        {

            string query = $"INSERT INTO `task`.`user`(`userName`,`password`,`email`,`IdStatus`,`totalhours`,`managerId`,`userComputer`) VALUES('{worker.WorkerName}','{worker.Password.ToUpper()}','{worker.Email}',{worker.StatusId},{worker.NumHoursWork},{worker.ManagerId},'{worker.WorkerComputer}'); ";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Get worker details by computer ip
        /// </summary>
        /// <param name="computerWorker">computer ip</param>
        /// <returns>worker instance</returns>
        public static Worker GetWorkerDetailsComputerWorker(string computerWorker)
        {
            string query = $"USE task;SELECT * FROM task.user JOIN task.status ON user.IdStatus=status.IdStatus WHERE userComputer='{computerWorker}'";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));

                }
                return workers;
            };

            List<Worker> workersLogin = DBAccess.RunReader(query, func);
            if (workersLogin != null && workersLogin.Count > 0)
            {

                return workersLogin[0];
            }
            return null;
        }

        /// <summary>
        /// send email to manager
        /// </summary>
        /// <param name="idWorker">id of worker who send the email</param>
        /// <param name="message">massage of email</param>
        /// <param name="subject">subject of email</param>
        /// <returns>true if succeeded, false if not</returns>
        public static bool sendEmailToManager(int idWorker, string message, string subject)
        {
            Worker manager = GetManager();
            Worker worker = GetWorkerDetails(idWorker);
            if (manager == null)
                return false;
            message += $"<br/><span style = 'color:red'> sincerly,{ worker.WorkerName}<span/>";
            return sendMessage(manager, message, subject);

        }

        /// <summary>
        /// Send message
        /// </summary>
        /// <param name="worker">worker who to send the email</param>
        /// <param name="message">message</param>
        /// <param name="subject">subject</param>
        /// <returns>true if succeeded, false if not</returns>
        public static bool sendMessage(Worker worker, string message, string subject)
        {

            if (worker == null)
                return false;
            SmtpClient client = new SmtpClient();
            client.DeliveryMethod = SmtpDeliveryMethod.Network;
            client.EnableSsl = true;
            client.Host = "smtp.gmail.com";
            client.Port = 587;
            System.Net.NetworkCredential credentials = new System.Net.NetworkCredential("task.FrishmanBerman@gmail.com", "task1234");
            client.UseDefaultCredentials = false;
            client.Credentials = credentials;
            MailMessage msg = new MailMessage();

            msg.From = new MailAddress("task.FrishmanBerman@gmail.com");
            msg.To.Add(new MailAddress(worker.Email));
            msg.Subject = subject;
            msg.IsBodyHtml = true;
            msg.Body = string.Format($"<html><body><p>{message}</br></p></body>");
            try
            {
                client.Send(msg);
                return true;
            }
            catch
            {
                return false;

            }
        }
    }
}



```
```csharp
using BOL.Convertors;
using BOL.HelpModel;
using DAL;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;

namespace BLL
{
    public class LogicTask
    {
        /// <summary>
        /// Add task to DB
        /// </summary>
        /// <param name="task">task instance to be added</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool AddTask(BOL.Models.Task task)
        {
            string query = $"INSERT INTO `task`.`task`(`reservingHours`,`givenHours`,`idProject`,`idUser`)VALUES({task.ReservingHours},{task.GivenHours },{task.IdProject},{task.IdWorker});";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Check if task already exists (with the same worker and project)
        /// </summary>
        /// <param name="task">task instance for checking</param>
        /// <returns>true if exists, false if not</returns>
        public static bool CheckIfExists(BOL.Models.Task task)
        {
            string query = $"SELECT * FROM task.task WHERE idProject={task.IdProject} and idUser={task.IdWorker};";
            List<BOL.Models.Task> projects = new List<BOL.Models.Task>();
            Func<MySqlDataReader, List<BOL.Models.Task>> func = (reader) =>
            {
                List<BOL.Models.Task> projectsWorker = new List<BOL.Models.Task>();
                while (reader.Read())
                {
                    projectsWorker.Add(ConvertorTask.convertToTask(reader));
                }
                return projectsWorker;
            };

            List<BOL.Models.Task> ProjectWorker = DBAccess.RunReader(query, func);
            if (ProjectWorker != null && ProjectWorker.Count > 0)
                return true;
            return false;
        }

        /// <summary>
        /// Get all tasks by worker id
        /// </summary>
        /// <param name="workerId">id of worker for searching</param>
        /// <returns>list of tasks witch belong to worker</returns>
        public static List<BOL.Models.Task> GetTasksWithWorkerAndProjectByWorkerId(int workerId)
        {
            string query = $"SELECT task.task.*,task.project.name,task.user.userName FROM task.task join task.user on task.user.idUser=task.task.idUser join task.project on task.project.idProject=task.task.idProject where task.task.idUser={workerId};";
            Func<MySqlDataReader, List<BOL.Models.Task>> func = (reader) =>
            {
                List<BOL.Models.Task> tasks = new List<BOL.Models.Task>();
                while (reader.Read())
                {
                    tasks.Add(ConvertorTask.convertToProjectWithProjectAndWorker(reader));
                }
                return tasks;
            };

            List<BOL.Models.Task> tasksList = DBAccess.RunReader(query, func);

            return tasksList;

        }

        /// <summary>
        /// Get all tasks by worker and project
        /// </summary>
        /// <param name="workerId">id of worker</param>
        /// <param name="projectId">id of project</param>
        /// <returns>list of tasks witch belong to project and worker</returns>
        public static BOL.Models.Task GetTaskByIdProjectAndIdWorker(int workerId, int projectId)
        {
            string query = $"SELECT * FROM task.task  where task.task.idUser={workerId} and task.task.idProject={projectId};";
            Func<MySqlDataReader, List<BOL.Models.Task>> func = (reader) =>
            {
                List<BOL.Models.Task> tasks = new List<BOL.Models.Task>();
                while (reader.Read())
                {
                    tasks.Add(ConvertorTask.convertToTask(reader));
                }
                return tasks;
            };

            List<BOL.Models.Task> tasksList = DBAccess.RunReader(query, func);

            return tasksList[0];

        }

        /// <summary>
        /// Get all tasks by project id
        /// </summary>
        /// <param name="workerId">id of project for searching</param>
        /// <returns>list of tasks witch belong to project</returns>
        public static List<BOL.Models.Task> GetTasksWithWorkerAndProjectByProjectId(int idProject)
        {
            string query = $"SELECT task.task.*,task.project.name,task.user.userName FROM task.task join task.user on task.user.idUser=task.task.idUser join task.project on task.project.idProject=task.task.idProject where task.task.idProject={idProject};";
            Func<MySqlDataReader, List<BOL.Models.Task>> func = (reader) =>
            {
                List<BOL.Models.Task> tasks = new List<BOL.Models.Task>();
                while (reader.Read())
                {
                    tasks.Add(ConvertorTask.convertToProjectWithProjectAndWorker(reader));
                }
                return tasks;
            };

            List<BOL.Models.Task> tasksList = DBAccess.RunReader(query, func);

            return tasksList;

        }

        /// <summary>
        /// Get the information from DB in order to view hours  charts
        /// </summary>
        /// <param name="projectId">the project to view the info for</param>
        /// <returns>dictionary KEY:string-workerName VALUE:hours-reserving and given hours</returns>
        public static Dictionary<string, Hours> GetWorkersDictionary(int projectId)
        {
            List<BOL.Models.Task> tasks = new List<BOL.Models.Task>();
            Dictionary<string, Hours> dictionary = new Dictionary<string, Hours>();
            tasks = GetTasksWithWorkerAndProjectByProjectId(projectId);
            foreach (BOL.Models.Task item in tasks)
            {
                dictionary.Add(item.workerName, new Hours { GivenHours = item.GivenHours, ReservingHours = item.ReservingHours });
            }
            return dictionary;
        }

        /// <summary>
        /// Get the information from DB in order to view hours  charts
        /// </summary>
        /// <param name="workerId">the worker to get information for </param>
        /// <returns>dictionary of KEY: string-workerName, VALUE:hours-reserving and given hours</returns>
        public static Dictionary<string, Hours> GetWorkerTasksDictionary(int workerId)
        {
            List<BOL.Models.Task> tasks = new List<BOL.Models.Task>();
            Dictionary<string, Hours> dictionary = new Dictionary<string, Hours>();
            tasks = GetTasksWithWorkerAndProjectByWorkerId(workerId);
            foreach (BOL.Models.Task item in tasks)
            {
                if (!dictionary.ContainsKey(item.projectName))
                    dictionary.Add(item.projectName, new Hours { GivenHours = item.GivenHours, ReservingHours = item.ReservingHours });
            }
            return dictionary;
        }

        /// <summary>
        /// Enable option of change amount of given or reserving hours for task
        /// </summary>
        /// <param name="task">the task to be changed</param>
        /// <returns>true if succeded, false if failed</returns>
        public static bool UpdateTask(BOL.Models.Task task)
        {
            string query = $"UPDATE `task`.`task` SET `reservingHours` = {task.ReservingHours},`givenHours` = {task.GivenHours} WHERE `idTask` = {task.IdTask};";
            return DBAccess.RunNonQuery(query) == 1;
        }


    }
}

```


```csharp
 using BOL;
using DAL;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;

namespace BLL
{
    public class LogicStatus
    {
        /// <summary>
        /// Get all statuses
        /// </summary>
        /// <returns>list of status</returns>
        public static List<Status> GetAllstatuses()
        {
            string query = $"SELECT * FROM task.status WHERE task.status.statusName!='Manager';";

            Func<MySqlDataReader, List<Status>> func = (reader) =>
            {
                List<Status> statuses = new List<Status>();
                while (reader.Read())
                {
                    statuses.Add(new Status
                    {
                        Id = reader.GetInt32(0),
                        StatusName = reader.GetString(1)
                    });
                }
                return statuses;
            };

            return DBAccess.RunReader(query, func);
        }
    }
}

```
```csharp
using BOL;
using BOL.Models;
using System;
using System.Collections.Generic;

namespace BLL
{
    public class LogicReports
    {

        /// <summary>
        /// Get report data
        /// </summary>
        /// <returns>list of reportData</returns>
        public static List<ReportData> CreateReport()
        {
            int id = 1;
            List<ReportData> reportDataList = new List<ReportData>();
            List<Project> projects = new List<Project>();
            projects = LogicProjects.GetAllProjects();
            foreach (Project project in projects)
            {
                int parentId = id++;
                decimal givenHoursOfProject = 0;
                List<Worker> workersOfProject = new List<Worker>();
                workersOfProject = LogicWorker.GetWorkersByProjectId(project.ProjectId);
                foreach (Worker worker in workersOfProject)
                {
                    Task task = new Task();
                    task = LogicTask.GetTaskByIdProjectAndIdWorker(worker.WorkerId, project.ProjectId);
                    ReportData reportData = new ReportData
                    {
                        Id = id++,
                        ParentId = parentId,
                        Name = worker.WorkerName,
                        TeamHeader = LogicWorker.GetWorkerDetails(project.IdTeamHead).WorkerName,
                        ReservingHours = task.ReservingHours,
                        GivenHours = task.GivenHours,
                        DateBegin = null,
                        DateEnd = null
                    };
                    givenHoursOfProject += reportData.GivenHours;
                    reportDataList.Add(reportData);
                }
                reportDataList.Add(new ReportData
                {
                    Id = parentId,
                    ParentId = 0,
                    Name = project.ProjectName,
                    TeamHeader = LogicWorker.GetWorkerDetails(project.IdTeamHead).WorkerName,
                    ReservingHours = project.QAHours + project.UIUXHours + project.DevHours,
                    GivenHours = givenHoursOfProject,
                    Customer = project.CustomerName,
                    DateBegin = project.DateBegin,
                    DateEnd = project.DateEnd,
                    Days = (project.DateEnd - project.DateBegin).Days,
                    WorkedDays = (DateTime.Now > project.DateEnd) ? (project.DateEnd - project.DateBegin).Days : (DateTime.Now - project.DateBegin).Days
                });

            }
            return reportDataList;
        }
        
    }
}

```
```csharp
using DAL;
using BOL;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Timers;
using BOL.Convertors;

namespace BLL
{
    public class LogicProjects
    {
        //timer for deadLine checking:
        private static Timer aTimer;

        /// <summary>
        /// Get all projects
        /// </summary>
        /// <returns>list of projects</returns>
        public static List<Project> GetAllProjects()
        {
            string query = $"SELECT * FROM task.project;";

            Func<MySqlDataReader, List<Project>> func = (reader) =>
            {
                List<Project> projects = new List<Project>();
                while (reader.Read())
                {
                    projects.Add(ConvertorProject.convertToProject(reader));
                }
                return projects;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get all projects witch their dead-line is tommorow
        /// </summary>
        /// <returns>list of projects that match the condition</returns>
        public static List<Project> GetAllProjectsByDeadLine()
        {
            string query = $"SELECT * FROM task.project where DATEDIFF(task.project.endDate,date(now()))=1;";

            Func<MySqlDataReader, List<Project>> func = (reader) =>
            {
                List<Project> projects = new List<Project>();
                while (reader.Read())
                {
                    projects.Add(ConvertorProject.convertToProject(reader));
                }
                return projects;
            };

            return DBAccess.RunReader(query, func);
        }

        /// <summary>
        /// Get all projects witch this worker included in
        /// </summary>
        /// <param name="workerId">id of worker</param>
        /// <returns>list of rrojects witch match the condition</returns>
        public static List<Project> GetAllProjectsByWorker(int workerId)
        {
            {
                string query = $"SELECT task.project.* FROM task.project join task.task on task.task.IdProject=task.project.idProject where task.task.idUser={workerId};";

                Func<MySqlDataReader, List<Project>> func = (reader) =>
                {
                    List<Project> projects = new List<Project>();
                    while (reader.Read())
                    {
                        projects.Add(ConvertorProject.convertToProject(reader));
                    }
                    return projects;
                };

                return DBAccess.RunReader(query, func);
            }
        }

        /// <summary>
        /// Get all projects witch belong to team head
        /// </summary>
        /// <param name="TeamHeadId">id of team head</param>
        /// <returns>list of projects witch match the condition</returns>
        public static List<Project> GetAllProjectsByTeamHead(int TeamHeadId)
        {
            {
                string query = $"SELECT * FROM task.project WHERE TeamHeadId={TeamHeadId};";

                Func<MySqlDataReader, List<Project>> func = (reader) =>
                {
                    List<Project> projects = new List<Project>();
                    while (reader.Read())
                    {
                        projects.Add(ConvertorProject.convertToProject(reader));
                    }
                    return projects;
                };

                return DBAccess.RunReader(query, func);
            }
        }

        /// <summary>
        /// Get project instance by project name
        /// </summary>
        /// <param name="projectName">name of project</param>
        /// <returns>project instance witch name was gotten</returns>
        public static Project GetProjectDetails(string projectName)
        {
            string query = $"SELECT * FROM task.project WHERE name='{projectName}'";
            Func<MySqlDataReader, List<Project>> func = (reader) =>
            {
                List<Project> projects = new List<Project>();
                while (reader.Read())
                {
                    projects.Add(ConvertorProject.convertToProject(reader));
                }
                return projects;
            };
            List<Project> proj = DBAccess.RunReader(query, func);
            if (proj != null && proj.Count > 0)
            {

                return proj[0];
            }
            return null;


        }

        /// <summary>
        /// Get project instance by project id
        /// </summary>
        /// <param name="projectName">id of project</param>
        /// <returns>project instance witch id was gotten</returns>
        public static Project GetProjectDetails(int projectId)
        {
            string query = $"SELECT * FROM task.project WHERE projectId={projectId}";
            Func<MySqlDataReader, List<Project>> func = (reader) =>
            {
                List<Project> projects = new List<Project>();
                while (reader.Read())
                {
                    projects.Add(ConvertorProject.convertToProject(reader));
                }
                return projects;
            };

            return (DBAccess.RunReader(query, func).Count() != 0 ? DBAccess.RunReader(query, func)[0] : null);

        }

        /// <summary>
        ///  Get precents of done part of current project
        /// </summary>
        /// <param name="projectId">id of project to search</param>
        /// <returns>num of precents</returns>
        public static decimal GetProjectState(int projectId)
        {
            string query = $"select sum(task.task.givenHours)*(task.project.QAHours+task.project.devHours+task.project.UIUXHours)/100 from task.task join task.project on task.project.idProject = task.task.idProject where task.task.idProject = {projectId}";
            return Convert.ToDecimal(DBAccess.RunScalar(query));
        }


        /// <summary>
        /// Delete project from DB
        /// </summary>
        /// <param name="projectName">project name for deleting</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool RemoveProject(string projectName)
        {
            string query = $"DELETE FROM task.hourfordepartment WHERE Name={projectName}";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Add project to DB
        /// </summary>
        /// <param name="project">project instance to be added</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool AddProject(Project project)
        {
            string dateBegin = project.DateBegin.ToString("yyy-MM-dd");
            string dateEnd = project.DateEnd.ToString("yyy-MM-dd");
            string query = $"INSERT INTO `task`.`project`(`name`,`startdate`,`Enddate`,`isFinished`,`customerName`,`DevHours`,`QAHours`,`UIUXHours`,`teamheadId`) VALUES('{project.ProjectName}','{dateBegin}','{dateEnd}',{project.IsFinish},'{project.CustomerName}',{project.DevHours},{project.QAHours},{project.UIUXHours},{project.IdTeamHead}); ";
            if (DBAccess.RunNonQuery(query) == 1)
            {
                Project currentProject = GetProjectDetails(project.ProjectName);
                foreach (BOL.Models.Task task in project.tasks)
                {
                    query = $"INSERT INTO `task`.`task`(`reservingHours`,`givenHours`,`idProject`,`idUser`)VALUES({task.ReservingHours},0,{currentProject.ProjectId},{task.IdWorker });";
                    DBAccess.RunNonQuery(query);
                }
                return true;
            }
            return false;

        }

        /// <summary>
        /// Check witch projects' end date is tommorow
        /// </summary>
        public static void CheckDeadLine()
        {
            List<Project> deadProjects = new List<Project>();
            deadProjects = GetAllProjectsByDeadLine();
            foreach (Project proj in deadProjects)
            {
                Worker teamHead = new Worker();
                teamHead = LogicWorker.GetWorkerDetails(proj.IdTeamHead);
                List<Worker> workers = new List<Worker>();
                workers = LogicWorker.GetWorkersByTeamhead(proj.IdTeamHead);
                LogicWorker.sendMessage(teamHead, $"Hi {teamHead.WorkerName}, <br/>Project: {proj.ProjectName} is about to reach the deadline tomorrow. This project is under your responsibility, please hurry up!!!", "ATTENTION");
                foreach (Worker worker in workers)
                {
                    LogicWorker.sendMessage(worker, $"Hi {worker.WorkerName}, <br/>Project: {proj.ProjectName} is about to reach the deadline tomorrow. you are subscribed to this project, please hurry up!!!", "ATTENTION");
                }

            }
        }
   
        /// <summary>
        /// raise timer that checks each part of time the dead-Line of projects 
        /// </summary>
        public static void RaiseTimer()
        {
            SetTimer();

            System.Diagnostics.Debug.WriteLine("\nPress the Enter key to exit the application...\n");
            System.Diagnostics.Debug.WriteLine("The application started at {0:HH:mm:ss.fff}", DateTime.Now);
            Console.ReadLine();
            aTimer.Stop();
            aTimer.Dispose();

            System.Diagnostics.Debug.WriteLine("Terminating the application...");
        }

        /// <summary>
        /// Set timer that checks the dead-line
        /// </summary>
        private static void SetTimer()
        {
            // Create a timer with a two second interval.
            aTimer = new Timer(1000 * 59);
            // Hook up the Elapsed event for the timer. 
            aTimer.Elapsed += OnTimedEvent;
            aTimer.AutoReset = true;
            aTimer.Enabled = true;
        }


        private static void OnTimedEvent(Object source, ElapsedEventArgs e)
        {
            System.Diagnostics.Debug.WriteLine("ll");

            if (DateTime.Now.ToShortTimeString() == "21:00")
                LogicProjects.CheckDeadLine();


        }
    }
}

```
```csharp
using DAL;
using BOL;
using BOL.Models;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;
using BOL.Convertors;

namespace BLL
{
   public class LogicPresentDay
    {

        /// <summary>
        /// get  all presentdays 
        /// </summary>

        /// <returns>list of PresentDays </returns>
        public static List<PresentDay> GetPresentByWorkerId(int idWorker)
        {
            string query = $"SELECT * FROM task.PresentDay WHERE task.presentDay.idUser={idWorker}";


            Func<MySqlDataReader, List<PresentDay>> func = (reader) =>
            {
                List<PresentDay> presentDays = new List<PresentDay>();
                while (reader.Read())
                {
                    presentDays.Add(new PresentDay
                    {
                        IdPresentDay = reader.GetInt32(0),
                        ProjectId = reader.GetInt32(1),
                        WorkerId = reader.GetInt32(2),
                        TimeBegin = reader.GetMySqlDateTime(3).GetDateTime(),
                        TimeEnd = reader.GetMySqlDateTime(4).GetDateTime(),
                        sumHoursDay = reader.GetInt32(5),
                        Comment = reader.GetString(6),
                        Description = reader.GetString(7)

                    });
                }
                return presentDays;
            };

            return DBAccess.RunReader(query, func);

        }

        /// <summary>
        /// get present day by following params:
        /// </summary>
        /// <param name="idWorker">id of worker</param>
        /// <param name="idProject"> id of project</param>
        /// <param name="dateBegin">begin date</param>
        /// <returns>PresentDay that was found</returns>
        public static PresentDay GetPresent(int idWorker,int idProject,DateTime dateBegin)
        {
            string query = $"SELECT * FROM task.PresentDay WHERE idproject={idProject} and iduser={idWorker} and startHour='{dateBegin.ToString("yyyy-MM-dd HH:mm:ss")}'";
            Func<MySqlDataReader, List<PresentDay>> func = (reader) =>
            {
                List<PresentDay> presentDays = new List<PresentDay>();
                while (reader.Read())
                {
                    presentDays.Add(new PresentDay
                    {
                        IdPresentDay = reader.GetInt32(0),
                        ProjectId = reader.GetInt32(1),
                        WorkerId = reader.GetInt32(2),
                        TimeBegin = reader.GetMySqlDateTime(3).GetDateTime(),
                        TimeEnd = reader.GetMySqlDateTime(4).GetDateTime(),
                        sumHoursDay = reader.GetInt32(5),
                        Comment = reader.GetString(6),
                        Description = reader.GetString(7)

                    });
                }
                return presentDays;
            };

            return DBAccess.RunReader(query, func)[0];
        }

        /// <summary>
        /// Get present day by id
        /// </summary>
        /// <param name="id">id of present day</param>
        /// <returns></returns>
        public static PresentDay GetPresentById(int id)
        {
            string query = $"SELECT * FROM task.PresentDay WHERE  IdpresentDay={id}";



            Func<MySqlDataReader, List<PresentDay>> func = (reader) =>
            {
                List<PresentDay> presentDays = new List<PresentDay>();
                while (reader.Read())
                {
                    presentDays.Add(new PresentDay
                    {  IdPresentDay=reader.GetInt32(0),
                        ProjectId = reader.GetInt32(1),
                        WorkerId = reader.GetInt32(2),
                        TimeBegin = reader.GetDateTime(3),
                        TimeEnd = reader.GetDateTime(4),
                        sumHoursDay = reader.GetInt32(5),
                        Comment=reader.GetString(6),
                        Description=reader.GetString(7)
                        
                    });
                }
                return presentDays;
            };

            return DBAccess.RunReader(query, func)[0];
        }
        

        /// <summary>
        /// Update present day's details
        /// </summary>
        /// <param name="presentDay">presentDay instance with details for updating</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool UpdatePresent(PresentDay presentDay)
        {
            PresentDay currentPresentDay = GetPresentById(presentDay.IdPresentDay);
            TimeSpan t = DateTime.Parse(presentDay.TimeEnd.ToLocalTime().ToString("yyyy-MM-dd HH:mm:ss")) - DateTime.Parse(currentPresentDay.TimeBegin.ToString("yyyy-MM-dd HH:mm:ss"));
            
            double addedHours = t.TotalHours;
               
            string query = $"UPDATE task.PresentDay SET EndHour='{presentDay.TimeEnd.ToLocalTime().ToString("yyyy-MM-dd HH:mm:ss")}',TotalHours={addedHours},comment='{presentDay.Comment}',description='{presentDay.Description}' WHERE IdPresentDay={presentDay.IdPresentDay}";
            if (DBAccess.RunNonQuery(query) == 1)
            {
                BOL.Models.Task currentTask = LogicTask.GetTaskByIdProjectAndIdWorker(currentPresentDay.WorkerId, currentPresentDay.ProjectId);
                currentTask.GivenHours +=(decimal)addedHours;
                if (LogicTask.UpdateTask(currentTask))
                {
                   Worker CurrentWorker =LogicWorker.GetWorkerDetails(currentPresentDay.WorkerId);
                    CurrentWorker.NumHoursWork +=(decimal) addedHours;
                  if(  LogicWorker.UpdateWorker(CurrentWorker))
                        return true;
                }
            }
            return false;
        }

        /// <summary>
        /// Add present day instance to DB
        /// </summary>
        /// <param name="presentDay">presentDay instance</param>
        /// <returns>id of added row if succeeded, 0 if failed</returns>
        public static int AddPresent(PresentDay presentDay)
        {
            string query = $"INSERT INTO `task`.`PresentDay`(`IdProject`,`IdUser`,`startHour`,`EndHour`,`Totalhours`,`comment`,`description`) VALUES({presentDay.ProjectId},{presentDay.WorkerId},'{presentDay.TimeBegin.ToLocalTime().ToString("yyyy-MM-dd HH:mm:ss")}','{presentDay.TimeEnd.ToLocalTime().ToString("yyyy-MM-dd HH:mm:ss")}',{presentDay.sumHoursDay},'',''); ";
            if (DBAccess.RunNonQuery(query) == 1)
            {
                try {
                return  GetPresent(presentDay.WorkerId, presentDay.ProjectId, presentDay.TimeBegin.ToLocalTime()).IdPresentDay;
                }
                catch
                {
                    return 0;
                }
            }
            return 0;


        }
        public static bool CheckifExists(PresentDay presentDay)
        {
            string query = $"SELECT * FROM task.presentday WHERE idProject={presentDay.ProjectId} and idUser={presentDay.WorkerId} and totalhours={0};";

            List<PresentDay> presents = new List<PresentDay>();
            Func<MySqlDataReader, List<PresentDay>> func = (reader) =>
            {
                List<PresentDay> presentsDay = new List<PresentDay>();
                while (reader.Read())
                {
                    presentsDay.Add(ConvertorPresentDay.convertDBtoPresentDay(reader));
                }
                return presentsDay;
            };

            List<PresentDay> PresentDay = DBAccess.RunReader(query, func);
            if (PresentDay != null && PresentDay.Count > 0)
                return true;
            return false;
        }
    }
}

```
```csharp
using BOL;
using BOL.Convertors;
using BOL.HelpModel;
using DAL;
using MySql.Data.MySqlClient;
using System;
using System.Collections.Generic;


namespace BLL
{
   public class LogicForgetPassword
    {
        /// <summary>
        /// Add new instance to fogotPassword table
        /// </summary>
        /// <param name="workerId">id worker to be added to DB</param>
        /// <returns>true if succeeded false if failed</returns>
        public static bool AddForgetPasswordRow(int workerId)
        {
            string query = $"INSERT INTO `task`.`forgetpassword`(`idForgetPassword`,`idUser`)VALUES('{Guid.NewGuid().ToString()}',{workerId}); ";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Check if fogotPassword table contains suitable instatce
        /// </summary>
        /// <param name="forgotPassword">ForgotPassword instance</param>
        /// <returns>worker id if found, 0 if not found</returns>
        public static int CheckRequestId(ForgotPassword forgotPassword)
        {
            string query = $"select task.forgetpassword.idUser from task.forgetpassword join task.user on task.forgetpassword.idUser=task.user.idUser where task.forgetpassword.IdForgetPassword = '{forgotPassword.IdForgetPassword}' and task.user.userName = '{forgotPassword.WorkerName}' limit 1";
           object result = DBAccess.RunScalar(query);
            int outRes;
            return result!=null ? int.TryParse(result.ToString(),out outRes)? int.Parse(DBAccess.RunScalar(query).ToString()) : 0:0;
        }

        /// <summary>
        /// Change password to the worker whose workerName is sent in ForgotPassword instance to the sent password 
        /// </summary>
        /// <param name="forgotPassword">ForgotPassword instance</param>
        /// <returns>null if succeeded, matching error if failed</returns>
        public static string ChangePassword(ForgotPassword forgotPassword)
        {
            int workerId = CheckRequestId(forgotPassword);
            if (workerId != 0)
            {
                Worker worker = LogicWorker.GetWorkerDetails(workerId);
                string newPasswordHash = forgotPassword.Password.ToUpper();
                if (!CheckIfPasswordExists(newPasswordHash))
                {
                    worker.Password = newPasswordHash;
                    if (LogicWorker.UpdatePassword(worker))
                    {
                        RemoveForgotPassword(forgotPassword.IdForgetPassword);
                        return null;
                    }
                    else return "did not succeed to save your password, try again.";
                }
                else return "Enter another password";
            }
            return "Do not try to change password!";
        }

        /// <summary>
        /// Check if password already exists in DB
        /// </summary>
        /// <param name="password">password for checking</param>
        /// <returns>true if found, false if not</returns>
        public static bool CheckIfPasswordExists(string password)
        {
            string query = $"SELECT * FROM task.user JOIN task.status ON task.user.IdStatus=task.status.IdStatus WHERE password='{password}';";

            Func<MySqlDataReader, List<Worker>> func = (reader) =>
            {
                List<Worker> workers = new List<Worker>();
                while (reader.Read())
                {
                    workers.Add(ConvertorWorker.convertDBtoWorker(reader));
                }
                return workers;
            };

            return DBAccess.RunReader(query, func).Count > 0 ? true : false;
        }

        /// <summary>
        /// Delete forgotPassword row from DB
        /// </summary>
        /// <param name="idForgotPassword">id of row</param>
        /// <returns>true if succeeded, false if failed</returns>
        public static bool RemoveForgotPassword(string idForgotPassword)
        {
            string query = $"DELETE FROM task.forgetPassword WHERE IdForgetPassword='{idForgotPassword}';";
            return DBAccess.RunNonQuery(query) == 1;
        }

        /// <summary>
        /// Get id of forgotPassword row that belongs to the current worker
        /// </summary>
        /// <param name="workerId">worker id to serch his request id</param>
        /// <returns>request id if found, 0 if not</returns>
        public static string GetIdForgetPassword(int workerId)
        {
            string query = $"select task.forgetpassword.IdForgetPassword from task.forgetpassword  where task.forgetpassword.idUser = {workerId}  limit 1";
            object result = DBAccess.RunScalar(query);
            return result != null ? result.ToString() : null;
        }
    }
}

```

### UIL
```csharp

using BOL;
using BLL;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using BOL.HelpModel;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{


    //--------------------------------
    [EnableCors("*", "*", "*")]
    public class WorkersController : ApiController
    {

     
        //get asll workers (manager-team heads- workers):
        [HttpGet]
        [Route("api/Workers/GetAllWorkers")]
        public HttpResponseMessage Get()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetAllWorkers());
        }

        //get all team heads:
        [HttpGet]
        [Route("api/Workers/GetAllTeamHeads")]
        public HttpResponseMessage GetAllTeamHeads()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetAllTeamHeads());
        }

        //get workers(DEV-QA-UIUX):
        [HttpGet]
        [Route("api/Workers/GetWorkers")]
        public HttpResponseMessage GetAllWorkers()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetWorkers());
        }
        //get workers(DEV-QA-UIUX):
        [HttpGet]
        [Route("api/Workers/GetWorker/{workerId}")]
        public HttpResponseMessage GetWorker(int workerId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetWorkerDetails(workerId));
        }

        //get all workers that are not belong to this team head (gets team head id):
        [HttpGet]
        [Route("api/Workers/GetAllowedWorkers/{teamHeadId}")]
        public HttpResponseMessage GetAllowedWorkers(int teamHeadId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetAllowedWorkers(teamHeadId));
        }

        //get all workers that are belong to this team head (gets team head id):
        [HttpGet]
        [Route("api/Workers/GetWorkersByTeamhead/{teamHeadId}")]
        public HttpResponseMessage GetWorkersByTeamhead(int teamHeadId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetWorkersByTeamhead(teamHeadId));
        }

        //get worker by id:
        [HttpGet]
        [Route("api/Workers/GetWorkerDetails/{id}")]
        public HttpResponseMessage Get(int id)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.GetWorkerDetails(id));
        }
        //send message to manager (gets EmailParams object that contains worker id, subject and message):
        [HttpPost]
        [Route("api/Workers/SendMessage")]
        public HttpResponseMessage sendMessage([FromBody]EmailParams emailParams)
        {
            Worker worker = LogicWorker.GetAllWorkers().Find(p => p.WorkerId == emailParams.idWorker);
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.sendMessage(worker, emailParams.message, emailParams.subject));
        }

        //send message to manager (gets EmailParams object that contains worker id, subject and message):
        [HttpPost]                                                       
        [Route("api/Workers/SendMessageToManager")]                        
        public HttpResponseMessage sendMessageToManager([FromBody]EmailParams emailParams)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicWorker.sendEmailToManager(emailParams.idWorker, emailParams.message, emailParams.subject));
        }

        //add worker to DB (gets worker object):
        [HttpPost]
        [Route("api/Workers/AddWorker")]
        public HttpResponseMessage Post([FromBody]Worker value)
        {
            if (ModelState.IsValid)
            {
                return (LogicWorker.AddWorker(value)) ?
                    Request.CreateResponse(HttpStatusCode.Created) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "Can not add to DB");
            };
            //if the code reached this part - the worker is not valid
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));
        }

        //login to system with worker name and password (gets LoginWorker object that contains name and password):
        [HttpPost]
        [Route("api/Workers/LoginByPassword")]
        public HttpResponseMessage LoginByPassword([FromBody]LoginWorker value)
        {
            if (ModelState.IsValid)
            {
                Worker worker = LogicWorker.GetWorkerDetailsByPassword(value.Password, value.WorkerName);
                //TODO:TOKEN
                return worker != null ?
                    Request.CreateResponse(HttpStatusCode.Created, worker) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "can not login with those details");

            };
            //if the code reached this part - the worker is not valid
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));

        }

        //login by computer (gets ComputerLogin object taht contains ComputerIp):
        [HttpPost]
        [Route("api/Workers/LoginByComputerWorker")]
        public HttpResponseMessage LoginByComputerWorker([FromBody]ComputerLogin computerLogin)
        {
            Worker worker = LogicWorker.GetWorkerDetailsComputerWorker(computerLogin.ComputerIp);
            return worker != null ?
                 Request.CreateResponse(HttpStatusCode.Created, worker) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "this ip address is not registered");

        }

        [HttpGet]
        [Route("api/Workers/ForgotPassword/{email}/{workerName}")]
        public HttpResponseMessage ForgotPassword([FromUri]string email,[FromUri] string workerName)
        {
            string result = LogicWorker.ForgotPassword(workerName, email);
            return  result==null?
                 Request.CreateResponse(HttpStatusCode.Created,"Email was sent successfully") :
                    Request.CreateResponse(HttpStatusCode.BadRequest, result);

        }

        //update worker details (gets Worker object for updating);
        [HttpPut]
        [Route("api/Workers/UpdateWorker")]
        public HttpResponseMessage UpdateWorker([FromBody]Worker value)
        {

            if (ModelState.IsValid)
            {
                return LogicWorker.UpdateWorker(value) ?
                     Request.CreateResponse(HttpStatusCode.Created) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "did not succeed to update");
            };
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));
        }

        //delete worker from DB (gets the workerId):
        [HttpDelete]
        [Route("api/Workers/RemoveWorker/{workerId}")]
        public HttpResponseMessage Delete(int workerId)
        {
            return LogicWorker.RemoveWorker(workerId) ?
                 Request.CreateResponse(HttpStatusCode.OK) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "Can not remove from DB");
        }

        //set new password to worker
        [HttpPost]
        [Route("api/Workers/SetNewPassword")]
        public HttpResponseMessage SetNewPassword([FromBody] ForgotPassword forgotPassword)
        {
            string result = LogicForgetPassword.ChangePassword(forgotPassword);
            return result == null ?
                Request.CreateResponse(HttpStatusCode.Created, "Saved your new password") :
                   Request.CreateResponse(HttpStatusCode.BadRequest, result);
        }

    }
}

```
```csharp
using BLL;
using BOL.Models;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{
    [EnableCors("*", "*", "*")]
    public class TaskController : ApiController
    {
        //add task to DB
        [HttpPost]
        [Route("api/Tasks/AddTask")]
        public HttpResponseMessage Post([FromBody] Task value)
        {
            if (ModelState.IsValid)
            {
                if (LogicTask.CheckIfExists(value))
                    return Request.CreateResponse(HttpStatusCode.BadRequest, "Worker already exists in this project.");
                return (LogicTask.AddTask(value)) ?
                    Request.CreateResponse(HttpStatusCode.Created) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "Can not add to DB.");
            };
            //if the code reached this part - the worker is not valid
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));

        }

        //get all tasks witch belong to project by project id:
        [HttpGet]
        [Route("api/Tasks/GetTasksWithWorkerAndProjectByProjectId/{projectId}")]
        public HttpResponseMessage GetTasksWithWorkerAndProjectByProjectId(int projectId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicTask.GetTasksWithWorkerAndProjectByProjectId(projectId));
        }

        //get all tasks witch belong to worker by worker id:
        [HttpGet]
        [Route("api/Tasks/GetTasksWithWorkerAndProjectByWorkerId/{workerId}")]
        public HttpResponseMessage GetTasksWithWorkerAndProjectByWorkerId(int workerId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicTask.GetTasksWithWorkerAndProjectByWorkerId(workerId));
        }
        
        [HttpGet]
        [Route("api/Tasks/GetWorkersDictionary/{projectId}")]
        public HttpResponseMessage GetWorkersDictionary(int projectId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicTask.GetWorkersDictionary(projectId));
        }

        //update task's details:
        [HttpPut]
        [Route("api/Tasks/UpdateTask")]
        public HttpResponseMessage UpdateTask([FromBody]Task value)
        {

            if (ModelState.IsValid)
            {
                return (LogicTask.UpdateTask(value)) ?
                     Request.CreateResponse(HttpStatusCode.Created) :
                    Request.CreateResponse(HttpStatusCode.BadRequest, "Can not update in DB");
            };
            //if the code reached this part - the worker is not valid
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));
        }

        [HttpGet]
        [Route("api/Tasks/GetWorkerTasksDictionary/{workerId}")]
        public HttpResponseMessage GetWorkerTasksDictionary(int workerId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicTask.GetWorkerTasksDictionary(workerId));
        }
    }
}

```
```csharp
using BLL;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{
    [EnableCors("*", "*", "*")]
    public class StatusController : ApiController
    {
        [HttpGet]
        [Route("api/Status/GetAllstatuses")]
        public HttpResponseMessage GetAllstatuses()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicStatus.GetAllstatuses());
        }

    }
}

```

```csharp
using BLL;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{
    [EnableCors("*", "*", "*")]
    public class ReportsController : ApiController
    {
        //get report data of projects with workers:
        [HttpGet]
        [Route("api/Reports/GetReportData")]
        public HttpResponseMessage GetReportData()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicReports.CreateReport());
        }
    
    }
}

```
```csharp

using BLL;
using BOL;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{
    [EnableCors("*", "*", "*")]
    public class ProjectsController : ApiController
    {
        //get all projects from DB
        [HttpGet]
        [Route("api/Projects/GetAllProjects")]
        public HttpResponseMessage GetAllProjects()
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicProjects.GetAllProjects());
        }

        //get all projects witch belong to team head by team head id:
        [HttpGet]
        [Route("api/Projects/GetAllProjectsByTeamHead/{TeamHeadId}")]
        public HttpResponseMessage GetAllProjectsByTeamHead(int teamHeadId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicProjects.GetAllProjectsByTeamHead(teamHeadId));
        }

        //get all projects witch belong to worker by worker id:
        [HttpGet]
        [Route("api/Projects/GetAllProjectsByWorker/{workerId}")]
        public HttpResponseMessage GetAllProjectsByWorker(int workerId)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicProjects.GetAllProjectsByWorker(workerId));
        }

    

        [HttpGet]
        [Route("api/Projects/GetProjectState/{idProject}")]
        public HttpResponseMessage GetProjectState(int idProject)
        {
            return Request.CreateResponse(HttpStatusCode.OK, LogicProjects.GetProjectState(idProject));
        }

        [HttpPost]
        [Route("api/Projects/AddProject")]
        public HttpResponseMessage AddProject([FromBody]Project value)
        {
        
            if (ModelState.IsValid)
            {
                return (LogicProjects.AddProject(value)) ?
                   Request.CreateResponse(HttpStatusCode.Created) :
                   Request.CreateResponse(HttpStatusCode.BadRequest, "Can not add to DB");
            };

            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));
        }


        [HttpDelete]
        [Route("api/Projects/RemoveProject")]
        public HttpResponseMessage Delete(string projectName)
        {
            return LogicProjects.RemoveProject(projectName) ?
                   Request.CreateResponse(HttpStatusCode.OK) :
                   Request.CreateResponse(HttpStatusCode.BadRequest, "Can not remove from DB");
        }
    }
}

```
```csharp
using BLL;
using BOL.Models;
using System.Net;
using System.Net.Http;
using System.Web.Http;
using System.Web.Http.Cors;

namespace webAPI_tasks.Controllers
{
    [EnableCors("*", "*", "*")]
    public class PresentDayController : ApiController
    {
       
        //add present day to DB
        [HttpPost]
        [Route("api/PresentDay/AddPresent")]
        public HttpResponseMessage AddPresent([FromBody]PresentDay value)
        {
            if (ModelState.IsValid)
            {
                if (LogicPresentDay.CheckifExists(value) == false)
                {
                    int id = LogicPresentDay.AddPresent(value);
                    return id != 0 ?
                          Request.CreateResponse(HttpStatusCode.Created, id) :
                          Request.CreateResponse(HttpStatusCode.BadRequest, "Can not add to DB");
                }
                else return Request.CreateResponse(HttpStatusCode.BadRequest, "you are logged in any where to this task");
            };
            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));

        }

        //update present day with end time 
        [HttpPut]
        [Route("api/PresentDay/UpdatePresentDay")]
        public HttpResponseMessage UpdatePresentDay([FromBody]PresentDay value)
        {
            if (ModelState.IsValid)
            {
                return LogicPresentDay.UpdatePresent(value) ?
                       Request.CreateResponse(HttpStatusCode.OK) :
                     Request.CreateResponse(HttpStatusCode.BadRequest, "Can not update in DB");

            };

            return Request.CreateResponse(HttpStatusCode.BadRequest, GetError.GetErrorsList(ModelState));

        }

        //Get all presents
        [HttpGet]
        [Route("api/PresentDay/GetPresentByWorkerId/{id}")]
        public HttpResponseMessage GetPresentByWorkerId(int id)
        {
           
            
                return Request.CreateResponse(HttpStatusCode.OK, LogicPresentDay.GetPresentByWorkerId(id));

           
            

        }

      

    }
}

```










