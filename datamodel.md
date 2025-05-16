📦 Supabase Data Model – Automated Life Organizer (ALO)

🔢 Enum Types
sql
Copy
Edit
CREATE TYPE task_status AS ENUM ('pending', 'completed', 'missed', 'deleted');
CREATE TYPE priority_level AS ENUM ('low', 'medium', 'high', 'urgent');
CREATE TYPE reminder_method AS ENUM ('push', 'email', 'sms');
CREATE TYPE mood_type AS ENUM ('energized', 'low', 'neutral', 'stressed', 'calm');
CREATE TYPE notification_type AS ENUM ('reminder', 'nudge', 'review', 'ai_suggestion');
CREATE TYPE integration_service AS ENUM ('google_calendar', 'notion', 'outlook', 'slack');
CREATE TYPE suggestion_trigger AS ENUM ('missed_task', 'mood_change', 'overload');
CREATE TYPE source_type AS ENUM ('manual', 'google', 'outlook', 'ical');
CREATE TYPE frequency_type AS ENUM ('daily', 'weekly', 'monthly');
🧑‍💼 users
Stores user account and preference data.

sql
Copy
Edit
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name TEXT,
  email TEXT UNIQUE NOT NULL,
  password_hash TEXT,
  timezone TEXT DEFAULT 'UTC',
  notification_preferences JSONB,
  mood_tracking_enabled BOOLEAN DEFAULT true,
  created_at TIMESTAMPTZ DEFAULT now(),
  updated_at TIMESTAMPTZ DEFAULT now()
);
🗂 task_categories
User-defined categories for organizing tasks.

sql
Copy
Edit
CREATE TABLE task_categories (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  name TEXT NOT NULL,
  color_code TEXT,
  icon TEXT,
  created_at TIMESTAMPTZ DEFAULT now()
);
✅ tasks
Tasks represent to-do items that may be scheduled, recurring, or tied to mood.

sql
Copy
Edit
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  title TEXT NOT NULL,
  description TEXT,
  status task_status DEFAULT 'pending',
  due_at TIMESTAMPTZ,
  completed_at TIMESTAMPTZ,
  priority priority_level DEFAULT 'medium',
  category_id UUID REFERENCES task_categories(id),
  created_at TIMESTAMPTZ DEFAULT now(),
  updated_at TIMESTAMPTZ DEFAULT now()
);
🔔 reminders
Reminders tied to tasks, controlling how and when users are nudged.

sql
Copy
Edit
CREATE TABLE reminders (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  task_id UUID REFERENCES tasks(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  reminder_time TIMESTAMPTZ NOT NULL,
  method reminder_method DEFAULT 'push',
  is_sent BOOLEAN DEFAULT false,
  snoozed_until TIMESTAMPTZ,
  created_at TIMESTAMPTZ DEFAULT now()
);
📅 events
Calendar events, either imported from integrations or created manually.

sql
Copy
Edit
CREATE TABLE events (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  title TEXT,
  description TEXT,
  start_time TIMESTAMPTZ NOT NULL,
  end_time TIMESTAMPTZ NOT NULL,
  location TEXT,
  source source_type DEFAULT 'manual',
  external_id TEXT,
  created_at TIMESTAMPTZ DEFAULT now()
);
🔁 recurring_rules
Defines recurring behavior for tasks or events.

sql
Copy
Edit
CREATE TABLE recurring_rules (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  task_id UUID REFERENCES tasks(id) ON DELETE CASCADE,
  frequency frequency_type NOT NULL,
  interval INT DEFAULT 1,
  count INT,
  until TIMESTAMPTZ,
  created_at TIMESTAMPTZ DEFAULT now()
);
🔌 integrations
Stores connected service tokens and metadata.

sql
Copy
Edit
CREATE TABLE integrations (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  service_name integration_service NOT NULL,
  access_token TEXT,
  refresh_token TEXT,
  token_expiry TIMESTAMPTZ,
  scopes TEXT[],
  created_at TIMESTAMPTZ DEFAULT now()
);
🌤️ mood_logs
Tracks user mood over time for personalized suggestions.

sql
Copy
Edit
CREATE TABLE mood_logs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  mood mood_type,
  notes TEXT,
  created_at TIMESTAMPTZ DEFAULT now()
);
📬 notifications
All notifications sent to users (reminders, reviews, AI messages, etc.).

sql
Copy
Edit
CREATE TABLE notifications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  related_task_id UUID REFERENCES tasks(id),
  message TEXT,
  type notification_type,
  channel reminder_method,
  sent_at TIMESTAMPTZ,
  acknowledged BOOLEAN DEFAULT false
);
⏱ focus_sessions
Pomodoro or deep work sessions linked to tasks.

sql
Copy
Edit
CREATE TABLE focus_sessions (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  task_id UUID REFERENCES tasks(id) ON DELETE SET NULL,
  start_time TIMESTAMPTZ NOT NULL,
  end_time TIMESTAMPTZ,
  duration_minutes INT,
  was_completed BOOLEAN,
  notes TEXT
);
🤖 ai_suggestion_log
Tracks AI-generated suggestions and their outcomes.

sql
Copy
Edit
CREATE TABLE ai_suggestion_log (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  suggested_action TEXT,
  related_task_id UUID REFERENCES tasks(id),
  outcome TEXT, -- 'accepted', 'rejected', 'ignored'
  triggered_by suggestion_trigger,
  created_at TIMESTAMPTZ DEFAULT now()
);
🗃️ Recommended Folder Structure
bash
Copy
Edit
/schema
  ├── enums.sql
  ├── users.sql
  ├── tasks.sql
  ├── reminders.sql
  └── ...
