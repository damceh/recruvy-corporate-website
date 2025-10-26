# PT. Recruvy International Group
## Phase 2 Development Plan - Job Portal System

**Document Version:** 1.0  
**Date:** October 2025  
**Current Status:** Phase 1 (Company Profile) Complete  
**Next Phase:** Job Portal with Application Management

---

## EXECUTIVE SUMMARY

Phase 2 transforms the static company profile into a **functional job portal** with candidate application management, job posting system, and basic CRM capabilities.

**Estimated Budget:** Rp 8.000.000 - Rp 15.000.000  
**Timeline:** 6-10 weeks  
**Complexity:** Medium to High

---

## PHASE 2 FEATURE CATEGORIES

### TIER 1: Essential Features (Must Have)
**Budget: ~5-7 juta | Priority: HIGH**

#### 1. Job Board System
**User Story:** HR can post jobs, candidates can browse and apply

Features:
- Admin dashboard untuk posting lowongan
- Job listing page (public)
- Job detail page dengan apply button
- Job categories & filters (industry, location, job type)
- Search functionality
- Job status management (Active, Closed, Draft)

Technical Requirements:
- Database: PostgreSQL or MongoDB
- Admin panel: Custom atau headless CMS
- File storage untuk job attachments

#### 2. Candidate Application System
**User Story:** Candidates can apply for jobs with CV upload

Features:
- Application form (nama, email, phone, CV upload)
- CV/Resume upload (PDF, max 5MB)
- Cover letter text area
- Application submission confirmation (email)
- Application tracking number

Technical Requirements:
- File upload handler (AWS S3, Cloudflare R2, or Supabase Storage)
- Email notification system (Resend, SendGrid, or Mailgun)
- Form validation & spam protection

#### 3. Basic Admin Dashboard
**User Story:** HR can view and manage applications

Features:
- Login system untuk admin
- List semua applications
- Filter by job, status, date
- View candidate details & CV
- Change application status (New, Reviewing, Shortlisted, Rejected, Hired)
- Export applications to CSV

Technical Requirements:
- Authentication system (session-based or JWT)
- Role-based access control (Admin only)
- Dashboard UI (React Admin, Retool, or custom)

---

### TIER 2: Enhanced Features (Should Have)
**Budget: ~3-5 juta | Priority: MEDIUM**

#### 4. Candidate Profile System
**User Story:** Candidates can create profile and track applications

Features:
- Candidate registration & login
- Profile creation (bio, skills, experience, education)
- Resume builder (optional)
- Application history tracking
- Saved jobs / bookmarks
- Email notifications for application updates

Technical Requirements:
- User authentication for candidates
- User database schema
- Password reset functionality
- Email service integration

#### 5. Advanced Job Features
**User Story:** Better job discovery and matching

Features:
- Job recommendations based on profile
- Similar jobs suggestions
- Job alerts via email (subscribe by category)
- Share job via social media
- Apply with LinkedIn profile (optional)
- Salary range display
- Company benefits listing

Technical Requirements:
- Email subscription system
- Basic matching algorithm
- Social sharing meta tags
- LinkedIn API integration (if needed)

#### 6. Enhanced Admin Tools
**User Story:** HR workflow improvement

Features:
- Bulk actions (reject/shortlist multiple)
- Application rating/scoring system
- Internal notes on candidates
- Interview scheduling (basic calendar)
- Email templates for candidate communication
- Analytics dashboard (views, applications, conversion rate)

Technical Requirements:
- Email templating system
- Basic analytics tracking
- Calendar integration (optional)

---

### TIER 3: Advanced Features (Nice to Have)
**Budget: ~5-8 juta | Priority: LOW (Future)**

#### 7. AI-Powered Features
- CV parsing & auto-fill form
- Job-candidate matching algorithm
- Automated candidate screening questions
- Chatbot untuk FAQ

#### 8. Advanced Communication
- In-app messaging between HR and candidates
- Video interview integration (Zoom/Google Meet)
- SMS notifications

#### 9. Multi-Company Portal
- Multiple client companies can post jobs
- Company profiles & branding
- Separate dashboards per company

#### 10. Payment Integration
- Featured job postings (paid)
- Premium candidate profiles
- Subscription model untuk companies

---

## TECHNICAL ARCHITECTURE

### Recommended Tech Stack for Phase 2

#### Option A: Full-Stack Framework (Recommended)
**Budget Impact:** Medium | **Timeline:** 6-8 weeks

**Frontend:**
- Astro + React islands (keep existing site)
- Or migrate to Next.js 14 (App Router)
- Tailwind CSS (existing)
- shadcn/ui for dashboard components

**Backend:**
- Next.js API Routes, atau
- Express.js + Node.js, atau
- Supabase (BaaS - Backend as a Service)

**Database:**
- PostgreSQL (Supabase, Railway, or Neon)
- Prisma ORM

**File Storage:**
- Supabase Storage (gratis 1GB), atau
- AWS S3, atau
- Cloudflare R2

**Authentication:**
- NextAuth.js, atau
- Supabase Auth, atau
- Clerk

**Email:**
- Resend (gratis 3000 emails/month), atau
- SendGrid, atau
- Mailgun

**Hosting:**
- Vercel (frontend + API)
- Railway atau Render (jika perlu dedicated backend)

**Cost Estimate:**
- Development: 8-12 juta
- Hosting: 200-500k/month

---

#### Option B: Low-Code Solution (Faster, Limited Customization)
**Budget Impact:** Lower | **Timeline:** 3-4 weeks

**Stack:**
- Keep Astro frontend
- Supabase untuk backend lengkap (DB + Auth + Storage + API)
- Retool atau Budibase untuk admin dashboard
- Zapier untuk automation

**Pros:**
- Faster development
- Lower initial cost (5-8 juta)
- Easy maintenance

**Cons:**
- Limited customization
- Vendor lock-in
- Scaling limitations

---

#### Option C: Headless CMS Approach
**Budget Impact:** Medium | **Timeline:** 5-7 weeks

**Stack:**
- Keep Astro frontend
- Strapi atau Payload CMS untuk backend
- PostgreSQL database
- Custom frontend untuk job board

**Pros:**
- Good content management
- API-first approach
- Flexible

**Cons:**
- Learning curve untuk CMS
- Might be overkill untuk job portal

---

## DATABASE SCHEMA (Basic)

### Core Tables Needed:

**1. jobs**
- id, title, description, company_name
- location, job_type, salary_range
- requirements, responsibilities
- status, posted_date, closing_date
- created_at, updated_at

**2. applications**
- id, job_id (FK), candidate_id (FK)
- name, email, phone
- cv_url, cover_letter
- status, applied_date
- created_at, updated_at

**3. users (admins)**
- id, email, password_hash, role
- created_at, updated_at

**4. candidates (if Tier 2)**
- id, email, password_hash
- name, phone, bio
- skills, experience, education
- resume_url, profile_complete
- created_at, updated_at

**5. saved_jobs (if Tier 2)**
- id, candidate_id (FK), job_id (FK)
- created_at

---

## DEVELOPMENT TIMELINE

### Week 1-2: Foundation
- Set up database & backend
- Implement authentication
- Create basic admin dashboard structure

### Week 3-4: Core Features
- Job posting CRUD operations
- Job listing & detail pages
- Application submission flow
- File upload implementation

### Week 5-6: Admin Features
- Application management interface
- Status workflow
- Email notifications
- CSV export

### Week 7-8: Testing & Polish
- Bug fixes
- Security audit
- Performance optimization
- User acceptance testing

### Week 9-10: Deployment & Training
- Production deployment
- Client training session
- Documentation handover
- Post-launch support

---

## BUDGET BREAKDOWN

### Development Costs (Tier 1 Only)

**Frontend Development:** Rp 2.000.000 - 3.000.000
- Job board UI
- Application forms
- Admin dashboard frontend

**Backend Development:** Rp 3.000.000 - 4.000.000
- Database setup
- API development
- Authentication
- File upload system
- Email integration

**Testing & QA:** Rp 500.000 - 1.000.000

**Deployment & Setup:** Rp 500.000 - 1.000.000

**Documentation & Training:** Rp 500.000

**Total (Tier 1):** Rp 6.500.000 - 9.500.000

### Add Tier 2 Features: +Rp 3.000.000 - 5.000.000

### Total Phase 2 (Tier 1 + 2): Rp 9.500.000 - 14.500.000

---

## RECURRING COSTS (Monthly)

**Hosting & Infrastructure:**
- Vercel Pro: ~$20/month (~300k)
- Database (Supabase/Railway): $10-25/month (~150-350k)
- File Storage: $5-10/month (~75-150k)
- Email service: $10-20/month (~150-300k)

**Total Monthly:** Rp 675.000 - 1.100.000/month

**Or Low-Budget Option:**
- Supabase Free tier (limit: 500MB DB, 1GB storage)
- Vercel Hobby (gratis, limit: 100GB bandwidth)
- Resend Free (3000 emails/month)

**Total Monthly (Free Tier):** Rp 0 - 300.000/month

---

## SECURITY CONSIDERATIONS

### Must Implement:
- HTTPS/SSL certificate
- Password hashing (bcrypt)
- SQL injection prevention (use ORM)
- XSS protection
- CSRF tokens
- Rate limiting on API endpoints
- File upload validation & scanning
- Secure file storage (private S3 bucket)
- Email verification
- Input sanitization
- Session security

### Recommended:
- Two-factor authentication for admin
- Backup automation (daily)
- Error logging & monitoring (Sentry)
- GDPR compliance (data deletion, privacy policy)

---

## RISK ASSESSMENT

### High Risk:
- **Scope creep:** Client minta fitur tambahan terus
  - Mitigation: Clear contract dengan feature list

- **Performance issues:** Database slow dengan data banyak
  - Mitigation: Proper indexing, pagination, caching

### Medium Risk:
- **File storage costs:** CV uploads mahal kalau banyak
  - Mitigation: Set file size limit, cleanup old applications

- **Email deliverability:** Email masuk spam
  - Mitigation: Proper SPF/DKIM setup, verified domain

### Low Risk:
- **Security breaches:** Unauthorized access
  - Mitigation: Follow security best practices above

---

## SUCCESS METRICS

### Technical KPIs:
- Page load time < 3 seconds
- Application submission success rate > 95%
- Admin dashboard uptime > 99.5%
- Zero critical security vulnerabilities

### Business KPIs:
- Number of jobs posted per month
- Number of applications received
- Time to hire reduction
- User satisfaction (admin feedback)

---

## MIGRATION PLAN (Phase 1 → Phase 2)

### Step 1: Preserve Current Site
- Create /jobs route for new job board
- Keep existing pages (Home, About, Services, Contact)
- Add "View Jobs" CTA on homepage

### Step 2: Gradual Rollout
- Launch with limited jobs (beta)
- Gather feedback
- Iterate based on usage

### Step 3: Full Launch
- Announce to clients
- Marketing push
- Monitor and support

---

## MAINTENANCE & SUPPORT

### Post-Launch Support (3 months):
- Bug fixes
- Minor feature adjustments
- Performance monitoring
- User support

**Cost:** Rp 1.500.000 - 2.500.000 (one-time)

### Ongoing Maintenance (Optional):
- Monthly updates
- Security patches
- Feature enhancements
- Technical support

**Cost:** Rp 500.000 - 1.500.000/month

---

## ALTERNATIVE: PHASED APPROACH

If budget is limited, break Phase 2 into smaller phases:

### Phase 2A: Job Board Only (Budget: 3-4 juta)
- Public job listings
- Basic job posting (admin)
- Simple application form (email only, no file upload)
- No login system

### Phase 2B: Application Management (Budget: 3-4 juta)
- CV upload
- Admin dashboard
- Application tracking
- Email notifications

### Phase 2C: Candidate Portal (Budget: 3-5 juta)
- Candidate registration
- Profile system
- Application history
- Saved jobs

---

## DECISION FACTORS

### Go with Phase 2 if:
✅ Client has consistent job posting needs (>5 jobs/month)
✅ Budget available: 8-15 juta
✅ Timeline: 2-3 months acceptable
✅ In-house job management needed

### Stick with Phase 1 if:
❌ Low volume of jobs (<3 jobs/month)
❌ Budget constraints
❌ Urgent timeline
❌ Can manage with email/WhatsApp for now

### Consider Third-Party if:
- Very high budget (>50 juta)
- Need enterprise features
- Multi-language support
- Complex integrations

---

## NEXT STEPS

1. **Client Meeting:** Present this plan, discuss priorities
2. **Budget Approval:** Get confirmation on budget range
3. **Tier Selection:** Choose Tier 1 only, or include Tier 2
4. **Tech Stack Decision:** Option A, B, or C
5. **Contract & Timeline:** Sign agreement with clear scope
6. **Kickoff:** Begin Phase 2 development

---

## APPENDIX

### Competitor Analysis
Research these platforms for feature inspiration:
- JobStreet Indonesia
- Glints
- Kalibrr
- LinkedIn Jobs

### Resources
- Astro Documentation: https://docs.astro.build
- Next.js Documentation: https://nextjs.org/docs
- Supabase Documentation: https://supabase.com/docs
- Tailwind CSS: https://tailwindcss.com

### Questions to Ask Client Before Phase 2

1. How many jobs do you expect to post per month?
2. Do you need candidate profiles, or just simple applications?
3. Will multiple people need admin access?
4. Do you need email notifications? For whom?
5. What's your monthly budget for hosting/services?
6. How long do you keep application data (GDPR consideration)?
7. Do you need reporting/analytics?
8. Integration with any existing systems (CRM, ATS)?

---

**Document prepared by:** Adam Almahdi  
**Contact for Phase 2 discussion:** [Contact Information]

---

## DOCUMENT STATUS

📋 **Review Status:** Reviewed - See FUTURE_DEVELOPMENT_REVIEW.md for detailed feedback

⚠️ **Important:** This document requires updates before client presentation:
- Complete database schema with ERD diagram
- Add data privacy & compliance section
- Add comprehensive testing strategy
- Revise budget estimates

📅 **Last Updated:** October 26, 2024  
📅 **Next Review:** Before Phase 2 kickoff