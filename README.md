student-management.student.oop

1. Adding new students.
2. Viewing student details (name, ID, and grades).
3. Calculating the average grade of a students.


// Define the Student class class Student 
  {constructor(id, name) 
  {this.id = id; this.name = name; this.grades = []; }

// Add a grade to the student's record
addGrade(grade) {
  if (grade >= 0 && grade <= 100) {
    this.grades.push(grade);
  } else {
    console.log("Grade should be between 0 and 100.");
  }
}

// Calculate the average grade
calculateAverage() {
  if (this.grades.length === 0) {
    return 0;
  }
  const total = this.grades.reduce((sum, grade) => sum + grade, 0);
  return (total / this.grades.length).toFixed(2);
}

// Get student details
getDetails() {
  return {
    id: this.id,
    name: this.name,
    grades: this.grades,
    average: this.calculateAverage(),
  };
}
}

// Define the Student Management System class class StudentManagementSystem
  {constructor() { this.students = []; }

// Add a new student
addStudent(id, name) {
  if (this.students.find(student => student.id === id)) {
    console.log("Student with this ID already exists.");
    return;
  }
  const newStudent = new Student(id, name);
  this.students.push(newStudent);
  console.log(`Student ${name} added successfully.`);
}

// View details of a student by ID
viewStudent(id) {
  const student = this.students.find(student => student.id === id);
  if (student) {
    console.log("Student Details:", student.getDetails());
  } else {
    console.log("Student not found.");
  }
}

// Add a grade for a student by ID
addGradeToStudent(id, grade) {
  const student = this.students.find(student => student.id === id);
  if (student) {
    student.addGrade(grade);
    console.log(`Grade ${grade} added to student ${student.name}.`);
  } else {
    console.log("Student not found.");
  }
}
}

// Test the system const system = new StudentManagementSystem();

// Add students system.addStudent(1, "John Doe"); system.addStudent(2, "Jane Smith");

// Add grades system.addGradeToStudent(1, 85); system.addGradeToStudent(1, 90); system.addGradeToStudent(2, 78);

// View student details system.viewStudent(1); system.viewStudent(2);
