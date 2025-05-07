Absolutely! Here is a professionally structured technical document that explains the functionality of each button click, the feature it supports, and how you will implement it in the JavaScript Object Model (JSOM). It includes technical explanations in words, a structured table, and relevant code snippets — all crafted to impress your mentor and present your work with clarity and confidence.

⸻

Technical Design Document for Library Management System (LMS)

1. Introduction

The Library Management System (LMS) is a web-based application designed to streamline library operations such as managing books, issuing and returning books, and maintaining member records. This document explains the functionality triggered by each button click and the underlying implementation approach using the JavaScript Object Model (JSOM). The goal is to ensure that each feature is technically explained, mapped to a button or action, and implemented efficiently using standard JavaScript DOM manipulation techniques.

⸻

2. Functional Overview

Each interactive element (e.g., button) in the LMS interface is associated with a distinct feature. The below table outlines the functionality triggered by each button, the technical operation expected, and the JSOM methods used for implementation.

2.1 Button-Feature Mapping Table

Button Label	Feature Description	Expected Behavior on Click	JSOM Concept Used
Add Book	Add a new book to catalog	Opens book form modal	getElementById, addEventListener
Edit Book	Update existing book info	Prefills form with selected book data	querySelectorAll, dataset, value
Delete Book	Remove book from catalog	Deletes the book entry from DOM	remove(), closest()
Add Member	Register a new member	Opens member registration form	addEventListener, modal display toggling
Edit Member	Modify existing member details	Displays prefilled editable member info	dataset, innerText, form value setting
Delete Member	Delete member record	Removes the member element from DOM	remove(), closest()
Issue Book	Issue a book to a member	Opens book-member mapping form	addEventListener, style.display
Return Book	Mark issued book as returned	Updates book status to “Available”	innerText, dataset, DOM update
Dashboard (Auto-load)	Overview of library stats	Auto-updates available/borrowed counts	window.onload, querySelectorAll()



⸻

3. Detailed Technical Description per Feature

⸻

3.1 Add Book Feature
	•	Objective: To allow the librarian to add a new book to the library catalog.
	•	UI Trigger: Add Book button.
	•	Technical Functionality:
	•	On click, a modal window (hidden initially) becomes visible using style.display = "block".
	•	The form fields allow input of Title, Author, and ISBN.
	•	JSOM Implementation:

document.getElementById("addBookBtn").addEventListener("click", function() {
    document.getElementById("bookModal").style.display = "block";
});

	•	DOM Concepts Used: getElementById, event handling via addEventListener, dynamic DOM style manipulation.

⸻

3.2 Edit Book Feature
	•	Objective: To update an existing book’s information.
	•	UI Trigger: Edit button beside each book entry.
	•	Technical Functionality:
	•	Each edit button holds the book’s ID in a data-id attribute.
	•	On click, book data is extracted from the DOM using the ID.
	•	The edit form is prefilled with current book info for modification.
	•	JSOM Implementation:

document.querySelectorAll(".edit-btn").forEach(function(button) {
    button.addEventListener("click", function() {
        var bookId = this.dataset.id;
        var bookTitle = document.getElementById("title-" + bookId).innerText;
        document.getElementById("editTitle").value = bookTitle;
        document.getElementById("editModal").style.display = "block";
    });
});

	•	DOM Concepts Used: querySelectorAll, dataset, innerText, value, dynamic DOM manipulation.

⸻

3.3 Delete Book Feature
	•	Objective: To permanently remove a book from the system.
	•	UI Trigger: Delete button beside each book.
	•	Technical Functionality:
	•	When clicked, the respective book’s HTML card is identified using closest().
	•	remove() is used to delete the node.
	•	JSOM Implementation:

document.querySelectorAll(".delete-btn").forEach(function(button) {
    button.addEventListener("click", function() {
        var bookCard = this.closest(".book-card");
        bookCard.remove();
    });
});

	•	DOM Concepts Used: Event delegation, closest(), node removal.

⸻

3.4 Add Member Feature
	•	Objective: To register a new member in the system.
	•	UI Trigger: Add Member button.
	•	Technical Functionality:
	•	Opens a modal form for entering new member details.
	•	JSOM Implementation:

document.getElementById("addMemberBtn").addEventListener("click", function() {
    document.getElementById("memberModal").style.display = "block";
});



⸻

3.5 Edit Member Feature
	•	Objective: To update a member’s personal details.
	•	Technical Functionality:
	•	Similar to Edit Book: member details are fetched using dataset.id.
	•	Prefilled values are displayed in an editable modal form.
	•	JSOM Implementation:

document.querySelectorAll(".edit-member-btn").forEach(function(button) {
    button.addEventListener("click", function() {
        var memberId = this.dataset.id;
        document.getElementById("editMemberName").value = document.getElementById("name-" + memberId).innerText;
        document.getElementById("editMemberModal").style.display = "block";
    });
});



⸻

3.6 Delete Member Feature
	•	Objective: To delete an existing member.
	•	Technical Functionality:
	•	The member’s card or row is removed from the DOM upon confirmation.
	•	JSOM Implementation:

document.querySelectorAll(".delete-member-btn").forEach(function(button) {
    button.addEventListener("click", function() {
        var memberCard = this.closest(".member-card");
        memberCard.remove();
    });
});



⸻

3.7 Issue Book Feature
	•	Objective: To issue a book to a member.
	•	UI Trigger: Issue Book button.
	•	Technical Functionality:
	•	Opens a modal to select a book and member.
	•	On submission, the book’s status is updated to “Issued”.
	•	JSOM Implementation:

document.getElementById("issueBookBtn").addEventListener("click", function() {
    document.getElementById("issueModal").style.display = "block";
});



⸻

3.8 Return Book Feature
	•	Objective: To mark a book as returned.
	•	UI Trigger: Return button next to issued books.
	•	Technical Functionality:
	•	Updates the book status in DOM from “Issued” to “Available”.
	•	JSOM Implementation:

document.querySelectorAll(".return-btn").forEach(function(button) {
    button.addEventListener("click", function() {
        var bookId = this.dataset.id;
        document.getElementById("status-" + bookId).innerText = "Available";
    });
});



⸻

3.9 Dashboard Feature
	•	Objective: Display statistics: total, available, and issued books.
	•	Technical Functionality:
	•	When the page loads, counts are dynamically calculated using class selectors.
	•	JSOM Implementation:

window.onload = function() {
    updateDashboard();
};

function updateDashboard() {
    var total = document.querySelectorAll(".book-card").length;
    var borrowed = document.querySelectorAll(".book-status.borrowed").length;
    document.getElementById("totalBooks").innerText = total;
    document.getElementById("borrowedBooks").innerText = borrowed;
    document.getElementById("availableBooks").innerText = total - borrowed;
}



⸻

4. Summary

This document serves as a blueprint for implementing all user-triggered actions in the Library Management System. It defines:
	•	What happens when a user clicks a button.
	•	The expected behavior in the browser.
	•	How the behavior is realized using core JSOM methods like getElementById, querySelectorAll, addEventListener, innerText, value, and DOM tree traversal and manipulation.

This clear structure and logic ensures maintainability, modularity, and clean code for an efficient front-end interface.

⸻

Would you like me to export this into a downloadable .docx or .pdf format for submission to your mentor?
