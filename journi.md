# MyFoundry API Feature - Customer Journey Map

---

## **RELEASE 2: Early Access (Manual Onboarding)**

### **Stage 1: AWARENESS**

**User receives early access invitation via direct email or 1-on-1 Account Manager contact**

- **Emotion:** Excited, Curious
- **Pain Point:** Unclear if feature solves their problem
- **What Happens:** Account Manager identifies user who previously requested API/custom dashboard features and sends personalized invitation
- **Content Delivered:** Brief email explaining what API access means and why they were selected
- **User Thinking:** "Great! They listened to our request. But what exactly can we do with this?"

---

### **Stage 2: INTEREST & DECISION**

**User has a call/meeting with Account Manager to learn about API benefits and decide to participate**

- **Emotion:** Hopeful, Slightly uncertain (technical concerns)
- **Pain Point:** Non-technical stakeholders worried about complexity - "Will our team understand how to use this?"
- **What Happens:** Account Manager explains:
  - What the API does in simple terms
  - How it solves their specific problem
  - Assures technical support will be provided
  - Addresses concerns about implementation complexity
- **Content Delivered:** Use-case examples relevant to their work (e.g., "Feed poverty data into Excel/Power BI for custom analysis")
- **User Thinking:** "OK, this could actually be useful. But I'm still nervous about the technical side"
- **Decision Point:** User agrees to participate in early access

---

### **Stage 3: ONBOARDING & ACCESS**

**User receives API documentation and access keys via email or secure portal**

- **Emotion:** Nervous, Ready to try
- **⚠️ Pain Point:** Technical documentation is too complex for non-technical stakeholders to understand
- **What Happens:**
  - Account Manager manually sends API keys
  - Technical documentation is attached (likely too technical)
  - User receives credentials and is ready to start
- **Content Delivered:**
  - API keys (unique to their account)
  - Step-by-step integration guide tailored to their use case
  - Simple numbered steps with screenshots
  - "Getting your first API call in 5 minutes" quick-start guide
  - Contact info for support if stuck
- **User Thinking:** "I have the keys... now what? This documentation looks scary. I hope someone can help us"
- **Critical Need:** Simplified guides that non-technical people can understand

---

### **Stage 4: INTEGRATION**

**User's development team (or technical person) attempts to integrate the API into their system**

- **Emotion:** Frustrated (if docs unclear) → Accomplished (if successful)
- **Pain Point:** Non-technical stakeholders feel left out of the process and can't support their dev team
- **What Happens:**
  - Developer/tech person reads documentation and attempts to implement
  - If stuck, optional 1-on-1 technical support call is available
  - Account Manager checks in to see if there are blockers
- **User's Dev Team Thinking:** "OK, let's try this... [reading docs] ... I have questions. I should reach out to support"
- **Non-Technical Stakeholder Thinking:** "Is it working yet? I hope they figure it out"
- **Checkpoint:** Track time to first successful API call - this tells us if our docs are working
- **Success Indicator:** User makes their first successful API call within reasonable time (e.g., 1-2 weeks)

---

### **Stage 5: USAGE & ACTIVATION**

**User successfully pulls data via API and starts building custom dashboards or feeding data into their systems**

- **Emotion:** Relief, Empowerment, Satisfaction
- **What Happens:**
  - Developer successfully retrieves data from MyFoundry API
  - Data flows into their custom tools (Power BI, Excel, etc.)
  - User creates their first custom report or dashboard using the API data
  - Non-technical stakeholders can now see the data they need without logging into MyFoundry
- **User Thinking:** "Yes! This is working. We can now analyze our data exactly how we need it"
- **Account Manager Does:** Check-in call - "How's it working? Any issues? What do you need next?"
- **Success Indicator:** ✅ Regular API calls happening (weekly/monthly depending on use case)
- **Next Step:** User becomes a reference customer for Release 3

---

## **RELEASE 3: Self-Service (API Key Generation)**

### **Stage 1: AWARENESS**

**User learns that API feature is now available to their subscription tier through multiple channels**

**Touchpoints:**
- 1-on-1 Account Manager outreach: "Your account now has API access"
- In-app notification banner: "New: Access our API directly"
- Email announcement: "Introducing API Access for all [Tier] subscribers"

- **Emotion:** Interested, Empowered (self-service option feels more accessible)
- **What Happens:** User sees announcement that API is now available to them without needing to request or wait
- **Message Conveyed:** "You now have API access! Generate your own keys in seconds without waiting for support"
- **User Thinking:** "Oh, API is available now? And I can set it up myself? That sounds easier than the manual process"
- **Non-Technical Manager Thinking:** "Finally, we can get this data without bugging Account Manager"

---

### **Stage 2: CONSIDERATION**

**User decides whether to use the feature based on their current needs**

**Touchpoint:** Account Manager explanation or in-app guide

- **Emotion:** Curious but hesitant
- **Pain Point:** "Will this actually be easy enough for us? Do we really need this?"
- **What Happens:**
  - User reads about API benefits
  - Considers if it's worth the effort to implement
  - Thinks about their current data access challenges
- **Content Delivered:** Use-case examples relevant to their sector:
  - "Analyze homelessness trends without logging in daily"
  - "Share poverty data with partner organizations"
  - "Create monthly reports automatically"
- **User Thinking:** "We do struggle with getting data into our reports. Maybe this is worth trying"
- **Decision Point:** User decides to proceed or delays decision

---

### **Stage 3: SELF-SERVICE SETUP**

**User generates their own API key directly from MyFoundry Dashboard without manual intervention**

**Touchpoint:** MyFoundry Dashboard → API Settings section

- **Emotion:** Confident, Independent
- **What Happens:**
  - User logs into MyFoundry
  - Navigates to API settings
  - Clicks "Generate API Key"
  - Simple 3-step wizard walks them through the process
  - Key is generated and displayed
- **UX Need:** The process must be so simple that even non-technical users understand
- **Pain Point:** Key management & security concerns - "How do I keep this safe?"
- **Solution:** Clear guidance:
  - "Keep this key private - treat it like a password"
  - "Anyone with your key can access your data"
  - Ability to regenerate key if compromised
  - Copy-to-clipboard button for ease
- **User Thinking:** "That was actually pretty easy. Now I have my key. What do I do with it?"
- **Success Indicator:** ✅ API key generated in <2 minutes
- **Non-Technical Stakeholder:** "Look, we got the key ourselves without waiting!"

---

### **Stage 4: INTEGRATION**

**User's development team reads step-by-step guides and integrates the API into their systems**

**Touchpoint:** Step-by-step integration guides (CRITICAL - this is where most users fail)

- **Emotion:** Nervous → Confident (if guide is good) / Frustrated (if guide is unclear)
- **⚠️ Pain Point:** Non-technical stakeholders still can't read technical API documentation and feel lost
- **What Happens:**
  - User downloads guide for their specific use case
  - Dev team follows numbered steps
  - Screenshots show exactly what they should see at each step
  - They test the API call and get data back
  - Non-technical person can understand at a high level what's happening
- **Multiple Guides Available (Not Just Raw API Docs):**
  - "Connect to Excel/Google Sheets - 10 minute guide"
  - "Feed into Power BI - Step-by-step"
  - "Basic Python integration for developers"
  - "Connect to [Their Specific Tool]"
- **Format:** 
  - Simple language (explain technical terms)
  - Step-by-step numbered instructions
  - Screenshots showing expected results
  - "Did you get stuck here? Click for help" sections
- **User Thinking:** "OK, we follow step 1... step 2... and boom, data appeared! It worked!"
- **Support Escalation:** If stuck after guide → Support ticket system or Account Manager
- **Success Indicator:** User successfully retrieves data via API within 1 week

---

### **Stage 5: USAGE & ONGOING**

**User successfully builds custom dashboards/reports and uses API regularly**

**Touchpoint:** Regular communication + support resources

- **Emotion:** Accomplished, Satisfied, Independent
- **What Happens:**
  - User's data is now flowing automatically via API
  - They build custom dashboards using the data
  - They no longer need to log into MyFoundry to access analysis
  - Non-technical stakeholders can see the data they need
- **User Thinking:** "This is working great. Our team is using it regularly. We're much more efficient now"
- **🎯 Adoption Metric:** We track % of subscribed users generating active API calls
- **Engagement:**
  - Monthly emails: "Your API usage stats" (shows # calls, data processed, etc.)
  - Success stories: "See how other authorities are using the API"
  - Newsletters: New data types available via API
- **Support Model:** 
  - Self-service help center (FAQs, common errors, troubleshooting)
  - Support tickets for complex issues
  - Community forum for peer help
- **Non-Technical Manager Thinking:** "Great, our team built this themselves and we're getting the data we need"
- **Account Manager Follow-up:** Quarterly check-ins - "How's the API working? Any new use cases?"

---

## **RELEASE 4: Self-Service API Portal**

### **Stage 1: AWARENESS**

**User discovers that a comprehensive, centralized API portal is now available**

**Touchpoints:**
- Newsletter announcement: "API Portal is Live - Everything in One Place"
- In-app banner: "Visit our new API Portal"
- Account Manager email: "You can now explore our API portal"

- **Emotion:** Interested, Empowered
- **What Happens:** User sees announcement that there's a dedicated portal with all API resources
- **Message Conveyed:** "Everything you need to integrate our API is now in one place - docs, tutorials, code samples, and more"
- **User Thinking:** "Great, they organized everything. Let me check it out"
- **Non-Technical Stakeholder:** "Maybe this will help me understand what our dev team is doing"

---

### **Stage 2: DISCOVERY**

**User visits the API Portal and explores what's available**

**Touchpoint:** Visit MyFoundry API Portal (dedicated website/section)

- **Emotion:** Curious, Maybe overwhelmed by options
- **What Happens:**
  - User lands on API Portal homepage
  - Sees different pathways for different user types
  - Browses available documentation and resources
  - Gets a sense of what's possible
- **Portal Must Include:**
  - Clear navigation with intuitive categories
  - Search functionality ("Search for 'Excel integration'")
  - Use-case filters ("Show me tutorials for homelessness data")
  - Visual guides indicating beginner/advanced content
- **User Thinking:** "OK, there's a lot here. Where do I even start?"
- **Navigation Example:**
  - "Getting Started" → "Tutorials" → "API Reference" → "Code Samples" → "Community"

---

### **Stage 3: EDUCATION** ⭐ **(CRITICAL STAGE)**

**Non-technical and technical users explore comprehensive documentation and learn about the API**

**Touchpoint:** API Portal with organized, accessible resources

- **Emotion:** Informed, Confident, Empowered
- **What Happens:** Users find content tailored to their skill level and needs

**For Non-Technical Users (Decision Makers, Managers):**
- "What is the API?" (simple, plain English explanation)
- "What can I do with it?" (use cases for their sector)
- "Do I need a developer?" (can we use pre-built integrations?)
- "How long does it take?" (time/effort required)
- "What does it cost?" (pricing/resource implications)

**For Technical Users (Developers, Engineers):**
- Complete API reference documentation
- Code examples in multiple languages (Python, JavaScript, etc.)
- SDKs if available
- Authentication details and security info
- Rate limits and best practices

**Interactive Learning Elements:**
- Live API sandbox/playground (try API calls without implementing)
- Copy-paste code snippets (ready to use)
- Try-before-you-implement demos
- Video library:
  - 5-minute "What is the API?" overview
  - Use-case walkthroughs (homelessness data, poverty analysis, etc.)
  - Common integration patterns
  - Troubleshooting videos

- **User Thinking (Non-Technical):** "OK, I understand what this does now. I can explain it to my team"
- **User Thinking (Technical):** "Great, I have examples to work from and a sandbox to test"
- **Emotion After:** Informed, Confident, Ready to implement

---

### **Stage 4: SELF-SETUP**

**User generates their own API key and prepares for implementation**

**Touchpoint:** API key generation + documentation auto-suggestion

- **Emotion:** Independent, Prepared, Excited
- **What Happens:**
  - User clicks "Generate API Key"
  - Simple wizard completes in <2 minutes
  - System auto-suggests relevant documentation based on their profile/use case
  - User downloads starter code or template
- **UX Flow:**
  - Generate key → Auto-suggest relevant guides → Download starter code → Bookmark support resources
- **Portal Helps:** "Based on your use case (homelessness analysis), here are the guides we recommend"
- **User Thinking:** "I have my key and I know exactly where to start"

---

### **Stage 5: IMPLEMENTATION**

**User's development team implements integration using multiple pathways available**

**Touchpoint:** Step-by-step guides + support community

- **Emotion:** Supported, Confident, Not alone
- **What Happens:** 
  - User chooses their integration path based on their tech stack
  - Follows guided steps
  - Tests in sandbox first
  - Gets help from community or support if needed

**Multiple Implementation Pathways Available:**
- ✅ **Quick Start Guides (5-10 min setup)** - "Get your first API call working in 5 minutes"
- ✅ **Integration Tutorials (step-by-step)** - For common tools (Excel, Power BI, Salesforce, etc.)
- ✅ **Code Samples (copy-paste ready)** - Real working examples they can adapt
- ✅ **Video Walkthroughs (for visual learners)** - Watch someone do it step-by-step
- ✅ **Community Forum (peer support)** - Ask other users who've done this

- **Support Escalation:**
  - If stuck after guides → Post in community forum
  - If issue persists → File support ticket
  - Premium support available for enterprise users
  
- **User's Dev Team Thinking:** "We have multiple ways to learn. If one doesn't work, we try another"
- **Non-Technical Person:** "Our team found the answer without waiting for support!"
- **Emotion Needed:** Supported, Not stuck, Empowered
- **Success Indicator:** Implementation completed within 1-2 weeks

---

### **Stage 6: USAGE & ADVOCACY**

**User uses API regularly, integrates into workflows, and becomes advocate for the feature**

**Touchpoint:** Ongoing engagement, success stories, community building

- **Emotion:** Accomplished, Satisfied, Proud of solution
- **What Happens:**
  - API is now core part of their data workflow
  - Custom dashboards automatically updated with latest data
  - Team efficiency improved
  - User shares success with peers/partners

- **🎯 Metric to Track:** % of subscribed users with active API calls (Adoption Rate)
  - Goal: Define target (e.g., 40% adoption within 6 months)
  - Track monthly to see growth

- **Ongoing Engagement:**
  - Monthly digest email: "Your API usage stats" (# calls, data processed, peak usage times)
  - Newsletter: "See how other authorities are using the API" (success stories)
  - Product updates: "New data types now available via API"
  - Feedback surveys: "How can we improve the API?"

- **Community Building:**
  - Feature high-performing users in case studies
  - Host monthly "API Office Hours" webinars
  - Recognize power users in newsletter

- **Upsell Opportunity:**
  - Premium API support tier for enterprise users
  - Priority support
  - Custom integration assistance

- **Advocacy & Growth:**
  - Encourage users to share their solutions with partner organizations
  - "Tell us how you're using the API" interviews
  - User testimonial videos for marketing
  - Referral incentives for bringing new users

- **User Thinking:** "This is working so well, we should tell other authorities about it"
- **Account Manager:** "I noticed you're using the API heavily. Would you be open to a case study?"
- **Success Indicator:** User is recommending MyFoundry to other organizations

---

## **CRITICAL SUCCESS FACTORS**

### **Release 2: Early Access**
- Account Manager provides hands-on support and personal guidance
- Simple step-by-step guides (not technical documentation)
- Track time-to-integration to identify pain points
- Clear communication: "We're here to help"

### **Release 3: Self-Service**
- Self-service key generation removes bottleneck
- Use-case specific guides (not raw API docs)
- Multiple format guides (text, screenshots, video)
- Adoption rate tracking shows feature is working

### **Release 4: API Portal**
- Comprehensive portal organized by skill level
- Video tutorials and interactive sandbox (hands-on learning)
- "Beginner Lane" for non-technical users
- Active community and support ecosystem

---

## **KEY METRICS TO TRACK (Adoption Rate)**

### **Release 2**
- # of early access users onboarded
- # who made first API call (within 30 days)
- Time to first successful API call
- Support tickets filed (indicates confusion)
- User satisfaction scores

### **Release 3**
- # of API keys self-generated (growth from R2)
- % of subscribed users with active API usage
- Adoption rate growth vs. R2 (target: 2x)
- Feature requests received (what do users want next?)
- Time to integration decreased?

### **Release 4**
- API portal traffic & engagement
- Most-visited documentation (what do users need most?)
- Sandbox usage (learning pathway effective?)
- Adoption rate target: ___ (define your goal)
- Community forum activity (peer support working?)
- Support ticket volume (reduced if docs are good)
