# 事件 Library 参考

Comprehensive list of events to track by business 类型 and context.

## Contents
- 营销 Site Events (navigation & engagement, CTA & form interactions, conversion events)
- 产品/App Events (onboarding, core usage, errors & support)
- Monetization Events (pricing & checkout, subscription management)
- E-commerce Events (browsing, cart, checkout, post-purchase)
- B2B / SaaS Specific Events (team & collaboration, integration events, 账户 events)
- 事件 Properties (Parameters)
- Funnel 事件 Sequences

## 营销 Site Events

### Navigation & Engagement

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| page_view | Page loaded (enhanced) | page_title, page_location, content_group |
| scroll_depth | User scrolled to threshold | depth (25, 50, 75, 100) |
| outbound_link_clicked | Click to external site | link_url, link_text |
| internal_link_clicked | Click within site | link_url, link_text, location |
| video_played | 视频 started | video_id, video_title, duration |
| video_completed | 视频 finished | video_id, video_title, duration |

### CTA & Form Interactions

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| cta_clicked | Call to action clicked | button_text, cta_location, page |
| form_started | User began form | form_name, form_location |
| form_field_completed | Field filled | form_name, field_name |
| form_submitted | Form successfully sent | form_name, form_location |
| form_error | Form validation failed | form_name, error_type |
| resource_downloaded | Asset downloaded | resource_name, resource_type |

### Conversion Events

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| signup_started | Initiated signup | 来源, page |
| signup_completed | Finished signup | method, plan, 来源 |
| demo_requested | Demo form submitted | company_size, industry |
| contact_submitted | Contact form sent | inquiry_type |
| newsletter_subscribed | Email list signup | 来源, list_name |
| trial_started | Free trial began | plan, 来源 |

---

## 产品/App Events

### Onboarding

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| signup_completed | 账户 created | method, referral_source |
| onboarding_started | Began onboarding | - |
| onboarding_step_completed | Step finished | step_number, step_name |
| onboarding_completed | All 步骤 done | steps_completed, time_to_complete |
| onboarding_skipped | User skipped onboarding | step_skipped_at |
| first_key_action_completed | Aha moment reached | action_type |

### Core Usage

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| session_started | App session began | session_number |
| feature_used | Feature interaction | feature_name, feature_category |
| action_completed | Core action done | action_type, count |
| content_created | User created content | content_type |
| content_edited | User modified content | content_type |
| content_deleted | User removed content | content_type |
| search_performed | In-app 搜索 | query, results_count |
| settings_changed | Settings modified | setting_name, new_value |
| invite_sent | User invited others | invite_type, count |

### Errors & Support

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| error_occurred | Error experienced | error_type, error_message, page |
| help_opened | Help accessed | help_type, page |
| support_contacted | Support request made | contact_method, issue_type |
| feedback_submitted | User feedback given | feedback_type, rating |

---

## Monetization Events

### Pricing & Checkout

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| pricing_viewed | 定价页 seen | 来源 |
| plan_selected | Plan chosen | plan_name, billing_cycle |
| checkout_started | Began checkout | plan, value |
| payment_info_entered | Payment submitted | payment_method |
| purchase_completed | Purchase successful | plan, value, currency, transaction_id |
| purchase_failed | Purchase failed | error_reason, plan |

### Subscription Management

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| trial_started | Trial began | plan, trial_length |
| trial_ended | Trial expired | plan, converted (bool) |
| subscription_upgraded | Plan upgraded | from_plan, to_plan, value |
| subscription_downgraded | Plan downgraded | from_plan, to_plan |
| subscription_cancelled | Cancelled | plan, reason, tenure |
| subscription_renewed | Renewed | plan, value |
| billing_updated | Payment method changed | - |

---

## E-commerce Events

### Browsing

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| product_viewed | 产品 page viewed | product_id, product_name, category, price |
| product_list_viewed | Category/list viewed | list_name, products[] |
| product_searched | 搜索 performed | query, results_count |
| product_filtered | Filters applied | filter_type, filter_value |
| product_sorted | Sort applied | sort_by, sort_order |

### Cart

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| product_added_to_cart | Item added | product_id, product_name, price, quantity |
| product_removed_from_cart | Item removed | product_id, product_name, price, quantity |
| cart_viewed | Cart page viewed | cart_value, items_count |

### Checkout

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| checkout_started | Checkout began | cart_value, items_count |
| checkout_step_completed | Step finished | step_number, step_name |
| shipping_info_entered | Address entered | shipping_method |
| payment_info_entered | Payment entered | payment_method |
| coupon_applied | Coupon used | coupon_code, discount_value |
| purchase_completed | Order placed | transaction_id, value, currency, items[] |

### Post-Purchase

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| order_confirmed | Confirmation viewed | transaction_id |
| refund_requested | Refund initiated | transaction_id, reason |
| refund_completed | Refund processed | transaction_id, value |
| review_submitted | 产品 reviewed | product_id, rating |

---

## B2B / SaaS Specific Events

### Team & Collaboration

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| team_created | New team/org made | team_size, plan |
| team_member_invited | Invite sent | role, invite_method |
| team_member_joined | Member accepted | role |
| team_member_removed | Member removed | role |
| role_changed | Permissions updated | user_id, old_role, new_role |

### Integration Events

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| integration_viewed | Integration page seen | integration_name |
| integration_started | 配置 began | integration_name |
| integration_connected | Successfully connected | integration_name |
| integration_disconnected | Removed integration | integration_name, reason |

### 账户 Events

| 事件 Name | 说明 | Properties |
|------------|-------------|------------|
| account_created | New 账户 | 来源, plan |
| account_upgraded | Plan upgrade | from_plan, to_plan |
| account_churned | 账户 closed | reason, tenure, mrr_lost |
| account_reactivated | Returned 客户 | previous_tenure, new_plan |

---

## 事件属性 (Parameters)

### 标准属性 to Include

**User Context:**
```
user_id: "12345"
user_type: "free" | "trial" | "paid"
account_id: "acct_123"
plan_type: "starter" | "pro" | "enterprise"
```

**Session Context:**
```
session_id: "sess_abc"
session_number: 5
page: "/pricing"
referrer: "https://google.com"
```

**广告活动 Context:**
```
source: "google"
medium: "cpc"
campaign: "spring_sale"
content: "hero_cta"
```

**产品 Context (E-commerce):**
```
product_id: "SKU123"
product_name: "Product Name"
category: "Category"
price: 99.99
quantity: 1
currency: "USD"
```

**Timing:**
```
timestamp: "2024-01-15T10:30:00Z"
time_on_page: 45
session_duration: 300
```

---

## Funnel 事件 Sequences

### Signup Funnel
1. signup_started
2. signup_step_completed (email)
3. signup_step_completed (password)
4. signup_completed
5. onboarding_started

### Purchase Funnel
1. pricing_viewed
2. plan_selected
3. checkout_started
4. payment_info_entered
5. purchase_completed

### E-commerce Funnel
1. product_viewed
2. product_added_to_cart
3. cart_viewed
4. checkout_started
5. shipping_info_entered
6. payment_info_entered
7. purchase_completed
