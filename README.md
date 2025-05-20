actor User
participant AppointmentSystem
participant Appointment

== Book Appointment ==

User -> AppointmentSystem : book_appointment(name, doctor, date, time)
AppointmentSystem -> Appointment : create instance
AppointmentSystem -> AppointmentSystem : store in appointments
AppointmentSystem -> User : print appointment ID

== View Appointment ==

User -> AppointmentSystem : view_appointment(id)
AppointmentSystem -> AppointmentSystem : get appointment from dict
alt if found
    AppointmentSystem -> Appointment : get_details()
    Appointment -> AppointmentSystem : return details
    AppointmentSystem -> User : print details
else not found
    AppointmentSystem -> User : print "Appointment not found"
end
