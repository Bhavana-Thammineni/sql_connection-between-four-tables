# sql_connection-between-four-tables
connection between four tables
-- task connection between four tables
CREATE TABLE department_hospital(
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(30) NOT NULL UNIQUE
);
CREATE TABLE doctor (
    doctor_id INT PRIMARY KEY AUTO_INCREMENT,
    doctor_name VARCHAR(30) NOT NULL,
    specialization VARCHAR(30),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES department(dept_id)
);
CREATE TABLE patient (
    patient_id INT PRIMARY KEY AUTO_INCREMENT,
    patient_name VARCHAR(30) NOT NULL,
    gender CHAR(1) CHECK (gender IN ('M','F')),
    dob DATE
);
CREATE TABLE appointment (
    appointment_id INT PRIMARY KEY AUTO_INCREMENT,
    doctor_id INT,
    patient_id INT,
    appointment_date DATE,
    status VARCHAR(20),
    FOREIGN KEY (doctor_id) REFERENCES doctor(doctor_id),
    FOREIGN KEY (patient_id) REFERENCES patient(patient_id)
);
