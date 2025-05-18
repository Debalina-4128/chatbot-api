🔧 System Overview
The system has 3 main components:

Retell AI Voice/Chat Agent – Handles user interaction via voice or chatbot.

FastAPI Backend – Hosts all logic and endpoints for booking, cancellation, knowledge base, and post-call logging.

Google Sheets Integration – Logs call/chat interactions after completion with metadata and summary.


Architecture Diagram:(./docs/architecture.png)


🔌 API Documentation:

POST /make_booking - Creates a new booking.

json
Copy
Edit
Request:
{
  "name": "Debalina",
  "date": "2025-05-21",
  "time": "18:30",
  "guests": 2,
  "contact": "9876543210"
}

POST /modify_booking - Modifies an existing booking.

json
Copy
Edit
{
  "contact": "9876543210",
  "new_date": "2025-05-22",
  "new_time": "19:00"
}
POST /cancel_booking
Cancels a booking by contact.

json
Copy
Edit
{
  "contact": "9876543210"
}


POST /log_conversation - Logs call/chat interaction post-completion.

json
Copy
Edit
{
  "modality": "Call",
  "call_time": "2025-05-17T17:30:00",
  "phone_number": "9876543210",
  "call_outcome": "AVAILABILITY",
  "room_name": "Executive Room",
  "booking_date": "2025-05-18",
  "booking_time": "15:00",
  "number_of_guests": 2,
  "call_summary": "User wanted to book a room for 2 guests tomorrow. Booking completed."
}


POST /search_knowledge_base - Searches through the knowledge base for relevant content.

json
Copy
Edit
{
  "query": "What are the check-in times?"
}


🛠️ Error Handling
If logging to Google Sheets fails, errors are captured in logs and sent to an error notification webhook (optional).

Booking endpoints return status codes for success and failure with messages.

✅ Technologies Used
Retell AI for voice/chat interface

FastAPI for backend logic

Google Sheets API for post-call logs

Uvicorn + Gunicorn for deployment

