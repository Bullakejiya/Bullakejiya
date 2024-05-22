public class Complaint
{
    public int Id { get; private set; }
    public string StdntName { get; set; }
 
    public string Title { get; set; }
   
    public DateTime Date { get; private set; }
   
    public bool isResolved { get; set; }
   


    public Complaint(int id, string studentName, string description)
    {
        Id = id;
        StdntName = studentName;
        Title = description;
        Date = DateTime.Now;
        isResolved = false;
    }
    public void MarkAsResolved()
    {
        isResolved = true;
    }
}

public class ComplaintManager
{
    public List<Complaint> complaints;

    public ComplaintManager()
    {
        complaints = new List<Complaint>();
    }


    public void AddComplaint(string studentName, string description)
    {
        int newId = complaints.Count + 1;
        Complaint newComplaint = new Complaint(newId, studentName, description);
        complaints.Add(newComplaint);
        Console.WriteLine("Complaint registered successfully.");
    }


    public void DisplayComplaints()
    {
        foreach (var complaint in complaints)
        {
            Console.WriteLine($" ID                  : {complaint.Id}\n Student             : {complaint.StdntName}\n Description         : {complaint.Title}\n Date                : {complaint.Date}\n Resolved            : {complaint.isResolved}\n");
        }
    }
    public Complaint GetComplaintById(int id)
    {
        return complaints.Find(c => c.Id == id);
    }
    public void UpdateComplaint(int id, string studentName, string description)
    {
        Complaint complaint = GetComplaintById(id);
        if (complaint != null)
        {
            complaint.StdntName = studentName;
            complaint.Title = description;
            Console.WriteLine("Complaint updated successfully.");
        }
        else
        {
            Console.WriteLine("Complaint not found.");
        }
    }
    public void DeleteComplaint(int id)
    {
        Complaint complaint = GetComplaintById(id);
        if (complaint != null)
        {
            complaints.Remove(complaint);
            Console.WriteLine("Complaint deleted successfully.");
        }
        else
        {
            Console.WriteLine("Complaint not found.");
        }
    }
}


    class complaint : ComplaintManager
{
    public static List<string> cmp = new List<string>();
    public static List<string> imp = new List<string>();
    public void cc()
    {
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("\n                                   CIET COMPLAINT MANAGEMENT SYSTEM\n");
    }
    public void dc()
    {
        Console.ForegroundColor= ConsoleColor.Yellow;
        Console.WriteLine("  1. Student ");
        Console.WriteLine();
        Console.WriteLine("  2. Faculty ");
        Console.WriteLine();
        Console.WriteLine("  3. Managemnt ");
        Console.WriteLine();
    }
}
class COMPLAINT : complaint
{
    public void bc()
    {
        bool exit = false;
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("              STUDENT LOGIN");
        while (!exit)
        {
            Console.ForegroundColor = ConsoleColor.Magenta;
            Console.WriteLine("\n1. Register Complaint");
            Console.WriteLine("\n2. Display Complaints");
            Console.WriteLine("\n3. Update Complaint");
            Console.WriteLine("\n4. Delete Complaint");
            Console.WriteLine("\n5. resolve complaint");
            Console.Write("\nEnter your choice    : ");
            int choice = int.Parse(Console.ReadLine());
            Console.Clear();
            if (choice == 1)
            {
                Console.ForegroundColor = ConsoleColor.Green;
                Console.Write("\nEnter student name   : ");
                string studentName = Console.ReadLine();
                Console.Write("\nEnter complaint Title: ");
                string Title = Console.ReadLine();
                Console.WriteLine();
                AddComplaint(studentName, Title);
                Console.WriteLine();
                break;
            }
            else if (choice == 2)
            {
                Console.ForegroundColor = ConsoleColor.White;
                DisplayComplaints();
                Console.WriteLine();
                break;
            }
            else if (choice == 3)
            {
                Console.ForegroundColor= ConsoleColor.White;
                DisplayComplaints();
                Console.ForegroundColor = ConsoleColor.Cyan;
                Console.Write("Enter ID to update   : ");
                int updateId = int.Parse(Console.ReadLine());
                Console.Clear();
                Console.Write("Enter the name           :  ");
                string STUDENT = Console.ReadLine();
                Console.Write("Enter new complaint Title: ");
                string newDescription = Console.ReadLine();
                UpdateComplaint(updateId, STUDENT, newDescription);
                Console.WriteLine();
                break;
            }
            else if (choice == 4)
            {
                Console.ForegroundColor = ConsoleColor.Blue;
                Console.Write("Enter complaint ID to delete: ");
                int deleteId = int.Parse(Console.ReadLine());
                DeleteComplaint(deleteId);
                Console.WriteLine();
                break;
            }
            else if (choice == 5)
            {
                Console.Write("Enter the complaint id : ");
                string id = Console.ReadLine();
                for (int i = 0; i < cmp.Count; i++)
                {
                    if (cmp[i] == id)
                    {
                        Console.ForegroundColor = ConsoleColor.DarkGreen;
                        Console.WriteLine("complaint resolved");
                        Console.WriteLine();
                        break;
                    }
                    else
                    {
                        Console.ForegroundColor = ConsoleColor.Red;
                        Console.WriteLine("complaint rejected");
                        Console.WriteLine();
                        break;
                    }
                }
                if (cmp.Count == 0)
                {
                    if (cmp[0] == id)
                    {
                        Console.ForegroundColor = ConsoleColor.DarkGreen;
                        Console.WriteLine("complaint resolved");
                        Console.WriteLine();
                        break;
                    }
                    else
                    {
                        Console.ForegroundColor = ConsoleColor.Red;
                        Console.WriteLine("complaint rejected");
                        Console.WriteLine();
                        break;
                    }
                }
                break;
            }
        }
    }
}
class FACULTY : COMPLAINT
{
    public static List<string> na = new List<string>();
    public static List<string> de = new List<string>();
    public static List<string> id = new List<string>();
    public static List<string> re = new List<string>();
    public static int count = 0;
    public void fac()
    {
        bool exit = false;
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("              FACULTY LOGIN");
        while (!exit)
        {
            Console.ForegroundColor = ConsoleColor.DarkMagenta;
            Console.WriteLine("\n1. Display students  Complaints");
            Console.WriteLine("\n2. Register Complaint");
            Console.WriteLine("\n3. Update Complaint");
            Console.WriteLine("\n4. Resolve Complaint");
            Console.Write("\nEnter your choice: ");
            int choice = int.Parse(Console.ReadLine());
            Console.Clear();
            if (choice == 2)
            {
                Console.ForegroundColor = ConsoleColor.Green;
                Console.Write("\nEnter faculty id     : ");
                string facid = Console.ReadLine();
                Console.Write("\nEnter faculty name   : ");
                string facName = Console.ReadLine();
                Console.Write("\nEnter complaint title: ");
                string description = Console.ReadLine();
                na.Add(facName);
                de.Add(description);
                id.Add(facid);
                re.Add("False");
                count++;
                Console.WriteLine("\nComplaint registered successfully.");
                Console.WriteLine();
                break;
            }
            else if (choice == 1)
            {
                Console.ForegroundColor = ConsoleColor.White;
                DisplayComplaints();
                break;
            }
            else if (choice == 3)
            {
                for (int i = 0; i < na.Count; i++)
                {
                    Console.ForegroundColor = ConsoleColor.White;
                    Console.WriteLine("Id                   :" + (i + 1));
                    Console.WriteLine("FacultyName          : " + na[i]);
                    Console.WriteLine("Title                : " + de[i]);
                    Console.WriteLine();
                }
                Console.ForegroundColor = ConsoleColor.Cyan;
                Console.Write("Enter  ID to update  : ");
                int updateId = int.Parse(Console.ReadLine());
                Console.Clear();
                Console.ForegroundColor = ConsoleColor.Magenta;
                Console.Write("Enter the name            :");
                string Faculty = Console.ReadLine();
                Console.Write("Enter new complaint title : ");
                string newDescription = Console.ReadLine();
                na[updateId-1] = Faculty;
                de[updateId-1] = newDescription;
                Console.WriteLine("Complaint updated successfully.");
                Console.WriteLine();
                break;
            }
            else if (choice == 4)
            {

                Console.Write("Enter complaint ID  ");
                string ID = Console.ReadLine();
                for (int i = 0; i < imp.Count; i++)
                {
                    if (imp[i] == ID)
                    {
                        Console.ForegroundColor = ConsoleColor.DarkGreen;
                        Console.WriteLine("complaint resolved");
                        Console.WriteLine();
                        break;
                    }
                    else
                    {
                        Console.ForegroundColor = ConsoleColor.Red;
                        Console.WriteLine("complaint rejected");
                        Console.WriteLine();
                        break;
                    }
                }
                if (imp.Count == 0)
                {
                    if (imp[0] == ID)
                    {
                        Console.ForegroundColor = ConsoleColor.DarkGreen;
                        Console.WriteLine("complaint resolved");
                        Console.WriteLine();
                        break;
                    }
                    else
                    {
                        Console.ForegroundColor = ConsoleColor.Red;
                        Console.WriteLine("complaint rejected");
                        Console.WriteLine();
                        break;
                    }
                }
            }
        }
    }
}
class A : FACULTY
{
    public void manage()
    {
        Console.ForegroundColor = ConsoleColor.Cyan;
        Console.WriteLine("              MANAGEMENT LOGIN");
        Console.WriteLine();
        Console.ForegroundColor = ConsoleColor.Red;
        Console.WriteLine(" \n1.  Complaints Applied by Students");
        Console.WriteLine(" \n2.  Complaints Applied by Faculty ");
        Console.ForegroundColor = ConsoleColor.Yellow;
        Console.Write("\n  Enter choice to display : ");
        int n = Convert.ToInt32(Console.ReadLine());
        Console.Clear();
        if (n == 1)
        {
            Console.ForegroundColor = ConsoleColor.White;
            DisplayComplaints();
            if (complaints != null)
            {
                Console.ForegroundColor = ConsoleColor.Magenta;
                Console.Write("Enter Complaint Id to resolve :");
                int i = Convert.ToInt32(Console.ReadLine());
                Console.WriteLine("   \n  1. Accept");
                Console.WriteLine("   \n   2. Reject");
                int p = Convert.ToInt32(Console.ReadLine());
                Console.Clear();
                if (p == 1)
                {
                    Console.ForegroundColor = ConsoleColor.Green;
                    Console.WriteLine("Complaint Resolved");
                    Console.WriteLine();
                    Console.ForegroundColor = ConsoleColor.Magenta;
                    Console.Write("Enter the id  resolved :");
                    cmp.Add(Console.ReadLine());

                }
                else if (p == 2)
                {
                    Console.ForegroundColor = ConsoleColor.Red;
                    Console.WriteLine("Complaint Rejected");
                    cmp.Add("0");
                }
                Console.Clear();
            }
            else if (complaints == null)
            {
                Console.ForegroundColor = ConsoleColor.Cyan;
                Console.WriteLine("  Complaints are Not Registered yet");
            }
        } 
        else  if (n == 2)
        {
            Console.ForegroundColor = ConsoleColor.White;
            for (int i = 0; i < na.Count; i++)
            {
                Console.WriteLine("Id           : " + (i + 1));
                Console.WriteLine("FacultyName  : " + na[i]);
                Console.WriteLine("Description  : " + de[i]);
                Console.WriteLine();
            }
            Console.ForegroundColor = ConsoleColor.Magenta;
            Console.WriteLine("Enter the id to resolve : ");
            int z = Convert.ToInt32(Console.ReadLine());
            Console.WriteLine(" \n 1. Accept");
            Console.WriteLine(" \n 2. Reject");
            int p = Convert.ToInt32(Console.ReadLine());
            Console.Clear();
            if (p == 1)
            {
                Console.ForegroundColor = ConsoleColor.Green;
                Console.WriteLine("Complaint Resolved");
                Console.WriteLine();
                Console.ForegroundColor = ConsoleColor.Magenta;
                Console.Write("Enter the id resolved :");
                imp.Add(Console.ReadLine());
            }
            else if (p == 2)
            {
                Console.ForegroundColor = ConsoleColor.Red;
                Console.WriteLine("Complaint Rejected");
                imp.Add("0");
            }
        }
        Console.Clear();
    }
}
class k
{
    public static void Main(string[] args)
    {
        A C = new A();
        C.cc();
        bool exitok = false;
        while (!exitok)
        {
            C.dc();
            int z = Convert.ToInt32(Console.ReadLine());
            Console.Clear();
            if (z == 3)
            {

                C.manage();

            }
            else if (z == 1)
            {
                C.bc();

            }
            else if (z == 2)
            {
                C.fac();

            }
            else
            {
                exitok = true;
                break;
            }
        }

    }
}
