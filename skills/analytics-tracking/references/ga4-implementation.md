# GA4 实施 参考

Detailed implementation guide for Google 分析 4.

## Contents
- Configuration (data streams, enhanced 衡量 events, recommended events)
- Custom Events (gtag.js implementation, Google Tag Manager)
- 转化 配置方式 (creating 转化, conversion values)
- Custom Dimensions and 指标 (适用场景, 配置方式 步骤, examples)
- Audiences (creating audiences, 受众 examples)
- 调试 (DebugView, real-time reports, 常见 issues)
- Data 质量 (filters, cross-domain 跟踪, session settings)
- Integration with Google Ads (linking, 受众 export)

## Configuration

### Data Streams

- One stream per 平台 (web, iOS, Android)
- Enable enhanced 衡量 for automatic 跟踪
- Configure data retention (2 months default, 14 months max)
- Enable Google Signals (for cross-device, if consented)

### Enhanced 衡量 Events (Automatic)

| 事件 | 说明 | Configuration |
|-------|-------------|---------------|
| page_view | Page loads | Automatic |
| scroll | 90% scroll depth | Toggle on/off |
| outbound_click | Click to external domain | Automatic |
| site_search | 搜索 query used | Configure parameter |
| video_engagement | YouTube 视频 plays | Toggle on/off |
| file_download | PDF, docs, etc. | Configurable extensions |

### Recommended Events

Use Google's predefined events when possible for enhanced reporting:

**All properties:**
- login, sign_up
- share
- 搜索

**E-commerce:**
- view_item, view_item_list
- add_to_cart, remove_from_cart
- begin_checkout
- add_payment_info
- purchase, refund

**Games:**
- level_up, unlock_achievement
- post_score, spend_virtual_currency

参考: https://support.google.com/分析/answer/9267735

---

## Custom Events

### gtag.js 实现

```javascript
// Basic event
gtag('event', 'signup_completed', {
  'method': 'email',
  'plan': 'free'
});

// Event with value
gtag('event', 'purchase', {
  'transaction_id': 'T12345',
  'value': 99.99,
  'currency': 'USD',
  'items': [{
    'item_id': 'SKU123',
    'item_name': 'Product Name',
    'price': 99.99
  }]
});

// User properties
gtag('set', 'user_properties', {
  'user_type': 'premium',
  'plan_name': 'pro'
});

// User ID (for logged-in users)
gtag('config', 'GA_MEASUREMENT_ID', {
  'user_id': 'USER_ID'
});
```

### Google 标签管理器 (dataLayer)

```javascript
// Custom event
dataLayer.push({
  'event': 'signup_completed',
  'method': 'email',
  'plan': 'free'
});

// Set user properties
dataLayer.push({
  'user_id': '12345',
  'user_type': 'premium'
});

// E-commerce purchase
dataLayer.push({
  'event': 'purchase',
  'ecommerce': {
    'transaction_id': 'T12345',
    'value': 99.99,
    'currency': 'USD',
    'items': [{
      'item_id': 'SKU123',
      'item_name': 'Product Name',
      'price': 99.99,
      'quantity': 1
    }]
  }
});

// Clear ecommerce before sending (best practice)
dataLayer.push({ ecommerce: null });
dataLayer.push({
  'event': 'view_item',
  'ecommerce': {
    // ...
  }
});
```

---

## 转化 配置方式

### Creating 转化

1. **Collect the 事件** - Ensure 事件 is firing in GA4
2. **Mark as conversion** - Admin > Events > Mark as conversion
3. **Set counting method**:
   - Once per session (leads, signups)
   - Every 事件 (purchases)
4. **Import to Google Ads** - For conversion-optimized bidding

### Conversion Values

```javascript
// Event with conversion value
gtag('event', 'purchase', {
  'value': 99.99,
  'currency': 'USD'
});
```

Or set default value in GA4 Admin when marking conversion.

---

## Custom Dimensions and 指标

### 适用场景

**Custom dimensions:**
- Properties you want to segment/filter by
- User attributes (plan 类型, industry)
- Content attributes (author, category)

**Custom 指标:**
- Numeric values to aggregate
- Scores, counts, durations

### 配置方式 步骤

1. Admin > Data 展示 > Custom definitions
2. Create dimension or metric
3. Choose scope:
   - **事件**: Per 事件 (content_type)
   - **User**: Per user (account_type)
   - **Item**: Per 产品 (product_category)
4. Enter parameter name (must match 事件 parameter)

### 示例

| Dimension | Scope | Parameter | 说明 |
|-----------|-------|-----------|-------------|
| User 类型 | User | user_type | Free, trial, paid |
| Content Author | 事件 | author | Blog post author |
| 产品 Category | Item | item_category | E-commerce category |

---

## Audiences

### Creating Audiences

Admin > Data 展示 > Audiences

**Use cases:**
- Remarketing audiences (export to Ads)
- Segment 分析
- Trigger-based events

### 受众 示例

**High-intent visitors:**
- Viewed 定价页
- Did not convert
- In last 7 days

**Engaged users:**
- 3+ sessions
- Or 5+ minutes total engagement

**Purchasers:**
- Purchase 事件
- For exclusion or lookalike

---

## 调试

### DebugView

Enable with:
- URL parameter: `?debug_mode=true`
- Chrome extension: GA Debugger
- gtag: `'debug_mode': true` in config

View at: Reports > Configure > DebugView

### Real-Time Reports

Check events within 30 minutes:
Reports > Real-time

### 常见问题

**Events not appearing:**
- Check DebugView first
- Verify gtag/GTM firing
- Check filter exclusions

**Parameter values missing:**
- Custom dimension not created
- Parameter name mismatch
- Data still processing (24-48 hrs)

**转化 not recording:**
- 事件 not marked as conversion
- 事件 name doesn't match
- Counting method (once vs. every)

---

## Data 质量

### Filters

Admin > Data streams > [Stream] > Configure tag settings > Define internal traffic

**Exclude:**
- Internal IP addresses
- Developer traffic
- 测试 environments

### Cross-Domain 跟踪

For multiple domains sharing 分析:

1. Admin > Data streams > [Stream] > Configure tag settings
2. Configure your domains
3. List all domains that should share sessions

### 会话 Settings

Admin > Data streams > [Stream] > Configure tag settings

- Session timeout (default 30 min)
- Engaged session duration (10 sec default)

---

## Integration with Google Ads

### Linking

1. Admin > 产品 links > Google Ads links
2. Enable auto-tagging in Google Ads
3. Import 转化 in Google Ads

### 受众 Export

Audiences created in GA4 can be used in Google Ads for:
- Remarketing 广告活动
- 客户 match
- Similar audiences
