{
  "baseSchema": {
    "name": "Social Productivity Dashboard",
    "description": "Phase 1 MVP - Social bookmark capture and task generation system",
    "tables": {
      "saves": {
        "name": "Social Saves",
        "description": "Captured social bookmarks and shared content",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Save ID"
          },
          "url": {
            "type": "url",
            "name": "Original URL",
            "description": "The original social media or web URL"
          },
          "title": {
            "type": "singleLineText",
            "name": "Content Title",
            "description": "Auto-extracted or manual title"
          },
          "description": {
            "type": "longText",
            "name": "Description",
            "description": "Content summary or user notes"
          },
          "platform": {
            "type": "singleSelect",
            "name": "Source Platform",
            "options": [
              { "name": "Instagram", "color": "pinkBright" },
              { "name": "YouTube", "color": "redBright" },
              { "name": "Pinterest", "color": "purpleBright" },
              { "name": "LinkedIn", "color": "blueBright" },
              { "name": "X (Twitter)", "color": "cyanBright" },
              { "name": "Google Feed", "color": "greenBright" },
              { "name": "Facebook", "color": "blueDark" },
              { "name": "Other", "color": "grayBright" }
            ]
          },
          "thumbnail": {
            "type": "attachment",
            "name": "Thumbnail Image",
            "description": "Auto-captured thumbnail or preview image"
          },
          "tags": {
            "type": "multipleSelects",
            "name": "Auto Tags",
            "description": "AI-generated tags from content analysis",
            "options": [
              { "name": "business", "color": "blueBright" },
              { "name": "productivity", "color": "greenBright" },
              { "name": "technology", "color": "purpleBright" },
              { "name": "marketing", "color": "orangeBright" },
              { "name": "design", "color": "pinkBright" },
              { "name": "development", "color": "cyanBright" },
              { "name": "inspiration", "color": "yellowBright" },
              { "name": "tutorial", "color": "redBright" },
              { "name": "research", "color": "grayBright" },
              { "name": "idea", "color": "tealBright" }
            ]
          },
          "created_date": {
            "type": "createdTime",
            "name": "Captured Date"
          },
          "status": {
            "type": "singleSelect",
            "name": "Processing Status",
            "options": [
              { "name": "New", "color": "blueBright" },
              { "name": "Processed", "color": "greenBright" },
              { "name": "Archived", "color": "grayBright" },
              { "name": "Deleted", "color": "redBright" }
            ]
          },
          "related_projects": {
            "type": "multipleRecordLinks",
            "name": "Related Projects",
            "linkedTableId": "projects"
          },
          "generated_tasks": {
            "type": "multipleRecordLinks",
            "name": "Generated Tasks",
            "linkedTableId": "tasks"
          },
          "ai_context": {
            "type": "longText",
            "name": "AI Processing Notes",
            "description": "AI analysis and context extraction"
          }
        }
      },
      "tasks": {
        "name": "Tasks",
        "description": "Generated and manual tasks from social saves and planning",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Task ID"
          },
          "title": {
            "type": "singleLineText",
            "name": "Task Title"
          },
          "description": {
            "type": "longText",
            "name": "Task Description"
          },
          "status": {
            "type": "singleSelect",
            "name": "Status",
            "options": [
              { "name": "To Do", "color": "blueBright" },
              { "name": "In Progress", "color": "yellowBright" },
              { "name": "Done", "color": "greenBright" },
              { "name": "Blocked", "color": "redBright" },
              { "name": "Cancelled", "color": "grayBright" }
            ]
          },
          "priority": {
            "type": "singleSelect",
            "name": "Priority",
            "options": [
              { "name": "Critical", "color": "redBright" },
              { "name": "High", "color": "orangeBright" },
              { "name": "Medium", "color": "yellowBright" },
              { "name": "Low", "color": "greenBright" }
            ]
          },
          "due_date": {
            "type": "date",
            "name": "Due Date",
            "options": {
              "dateFormat": { "name": "us" },
              "timeFormat": { "name": "12hour" }
            }
          },
          "estimated_hours": {
            "type": "number",
            "name": "Estimated Hours",
            "options": {
              "precision": 1
            }
          },
          "actual_hours": {
            "type": "number",
            "name": "Actual Hours",
            "options": {
              "precision": 1
            }
          },
          "source_save": {
            "type": "multipleRecordLinks",
            "name": "Source Save",
            "linkedTableId": "saves"
          },
          "project": {
            "type": "multipleRecordLinks",
            "name": "Project",
            "linkedTableId": "projects"
          },
          "created_date": {
            "type": "createdTime",
            "name": "Created Date"
          },
          "completed_date": {
            "type": "date",
            "name": "Completed Date"
          },
          "ai_generated": {
            "type": "checkbox",
            "name": "AI Generated",
            "description": "Whether this task was generated by AI from a social save"
          },
          "generation_prompt": {
            "type": "longText",
            "name": "AI Generation Context",
            "description": "The prompt and context used to generate this task"
          }
        }
      },
      "projects": {
        "name": "Projects",
        "description": "Ongoing initiatives and business projects",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Project ID"
          },
          "name": {
            "type": "singleLineText",
            "name": "Project Name"
          },
          "description": {
            "type": "longText",
            "name": "Project Description"
          },
          "status": {
            "type": "singleSelect",
            "name": "Project Status",
            "options": [
              { "name": "Planning", "color": "blueBright" },
              { "name": "Active", "color": "greenBright" },
              { "name": "On Hold", "color": "yellowBright" },
              { "name": "Completed", "color": "purpleBright" },
              { "name": "Cancelled", "color": "redBright" }
            ]
          },
          "priority": {
            "type": "singleSelect",
            "name": "Priority",
            "options": [
              { "name": "High", "color": "redBright" },
              { "name": "Medium", "color": "yellowBright" },
              { "name": "Low", "color": "greenBright" }
            ]
          },
          "start_date": {
            "type": "date",
            "name": "Start Date"
          },
          "target_date": {
            "type": "date",
            "name": "Target Completion Date"
          },
          "related_saves": {
            "type": "multipleRecordLinks",
            "name": "Related Saves",
            "linkedTableId": "saves"
          },
          "project_tasks": {
            "type": "multipleRecordLinks",
            "name": "Project Tasks",
            "linkedTableId": "tasks"
          },
          "whimsical_board": {
            "type": "url",
            "name": "Whimsical Board URL",
            "description": "Link to visual planning board"
          },
          "notes": {
            "type": "multipleRecordLinks",
            "name": "Project Notes",
            "linkedTableId": "notes"
          },
          "created_date": {
            "type": "createdTime",
            "name": "Created Date"
          }
        }
      },
      "notes": {
        "name": "Notes",
        "description": "Linked notes and documentation",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Note ID"
          },
          "title": {
            "type": "singleLineText",
            "name": "Note Title"
          },
          "content": {
            "type": "longText",
            "name": "Note Content"
          },
          "note_type": {
            "type": "singleSelect",
            "name": "Note Type",
            "options": [
              { "name": "Meeting Notes", "color": "blueBright" },
              { "name": "Idea", "color": "purpleBright" },
              { "name": "Research", "color": "greenBright" },
              { "name": "Reference", "color": "orangeBright" },
              { "name": "Decision Log", "color": "redBright" },
              { "name": "Planning", "color": "yellowBright" }
            ]
          },
          "related_saves": {
            "type": "multipleRecordLinks",
            "name": "Related Saves",
            "linkedTableId": "saves"
          },
          "related_tasks": {
            "type": "multipleRecordLinks",
            "name": "Related Tasks",
            "linkedTableId": "tasks"
          },
          "related_projects": {
            "type": "multipleRecordLinks",
            "name": "Related Projects",
            "linkedTableId": "projects"
          },
          "created_date": {
            "type": "createdTime",
            "name": "Created Date"
          },
          "modified_date": {
            "type": "lastModifiedTime",
            "name": "Last Modified"
          }
        }
      },
      "prompts": {
        "name": "AI Prompts",
        "description": "Library of AI prompts for task generation and processing",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Prompt ID"
          },
          "name": {
            "type": "singleLineText",
            "name": "Prompt Name"
          },
          "prompt_text": {
            "type": "longText",
            "name": "Prompt Template"
          },
          "category": {
            "type": "singleSelect",
            "name": "Category",
            "options": [
              { "name": "Task Generation", "color": "blueBright" },
              { "name": "Content Analysis", "color": "greenBright" },
              { "name": "Planning", "color": "purpleBright" },
              { "name": "Summarization", "color": "orangeBright" },
              { "name": "Research", "color": "yellowBright" }
            ]
          },
          "variables": {
            "type": "longText",
            "name": "Required Variables",
            "description": "List of variables this prompt expects"
          },
          "usage_count": {
            "type": "number",
            "name": "Usage Count"
          },
          "success_rate": {
            "type": "percent",
            "name": "Success Rate"
          },
          "created_date": {
            "type": "createdTime",
            "name": "Created Date"
          }
        }
      },
      "focus_logs": {
        "name": "Focus Sessions",
        "description": "Time tracking and productivity sessions",
        "fields": {
          "id": {
            "type": "autoNumber",
            "name": "Session ID"
          },
          "session_date": {
            "type": "date",
            "name": "Session Date"
          },
          "start_time": {
            "type": "dateTime",
            "name": "Start Time"
          },
          "end_time": {
            "type": "dateTime",
            "name": "End Time"
          },
          "duration_minutes": {
            "type": "number",
            "name": "Duration (Minutes)"
          },
          "focus_type": {
            "type": "singleSelect",
            "name": "Focus Type",
            "options": [
              { "name": "Deep Work", "color": "blueBright" },
              { "name": "Planning", "color": "purpleBright" },
              { "name": "Learning", "color": "greenBright" },
              { "name": "Admin", "color": "orangeBright" },
              { "name": "Creative", "color": "pinkBright" }
            ]
          },
          "related_project": {
            "type": "multipleRecordLinks",
            "name": "Related Project",
            "linkedTableId": "projects"
          },
          "related_tasks": {
            "type": "multipleRecordLinks",
            "name": "Tasks Worked On",
            "linkedTableId": "tasks"
          },
          "productivity_score": {
            "type": "rating",
            "name": "Productivity Score",
            "options": {
              "icon": "star",
              "max": 5,
              "color": "yellowBright"
            }
          },
          "notes": {
            "type": "longText",
            "name": "Session Notes"
          }
        }
      }
    }
  },
  "sampleData": {
    "saves": [
      {
        "url": "https://www.youtube.com/watch?v=example",
        "title": "How to Build Productivity Systems",
        "description": "Great video about building personal productivity workflows",
        "platform": "YouTube",
        "tags": ["productivity", "tutorial"],
        "status": "New"
      },
      {
        "url": "https://www.instagram.com/p/example",
        "title": "Morning Routine for Entrepreneurs",
        "description": "Instagram post about effective morning routines",
        "platform": "Instagram",
        "tags": ["business", "productivity"],
        "status": "Processed"
      }
    ],
    "tasks": [
      {
        "title": "Research productivity app competitors",
        "description": "Analyze existing productivity apps to identify gaps and opportunities",
        "status": "To Do",
        "priority": "High",
        "estimated_hours": 4,
        "ai_generated": true
      },
      {
        "title": "Set up Airtable base structure",
        "description": "Create the foundational database structure for the productivity system",
        "status": "In Progress",
        "priority": "Critical",
        "estimated_hours": 2
      }
    ],
    "projects": [
      {
        "name": "Social Productivity Dashboard MVP",
        "description": "Phase 1 development of the social bookmark productivity system",
        "status": "Active",
        "priority": "High"
      }
    ]
  }
}