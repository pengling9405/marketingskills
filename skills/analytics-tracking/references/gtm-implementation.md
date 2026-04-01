# Google 标签管理器 实现 参考

Detailed guide for implementing 跟踪 via Google Tag Manager.

## Contents
- Container Structure (tags, triggers, variables)
- Naming Conventions
- Data Layer Patterns
- 常见 Tag Configurations (GA4 configuration tag, GA4 事件 tag, Facebook pixel)
- Preview and Debug
- Workspaces and Versioning
- Consent Management
- Advanced Patterns (tag sequencing, exception handling, custom JavaScript variables)

## Container Structure

### Tags

Tags are code snippets that execute when triggered.

**常见 tag types:**
- GA4 Configuration (base 配置)
- GA4 事件 (custom events)
- Google Ads Conversion
- Facebook Pixel
- LinkedIn Insight Tag
- Custom HTML (for other pixels)

### Triggers

Triggers define when tags fire.

**Built-in triggers:**
- 页面浏览: All Pages, DOM Ready, Window Loaded
- Click: All Elements, Just Links
- Form Submission
- Scroll Depth
- Timer
- Element Visibility

**Custom triggers:**
- Custom 事件 (from dataLayer)
- Trigger Groups (multiple conditions)

### Variables

Variables capture dynamic values.

**Built-in (enable as needed):**
- Click Text, Click URL, Click ID, Click Classes
- Page Path, Page URL, Page Hostname
- Referrer
- Form Element, Form ID

**User-defined:**
- Data Layer variables
- JavaScript variables
- Lookup tables
- RegEx tables
- Constants

---

## Naming Conventions

### 推荐格式

```
[Type] - [Description] - [Detail]

Tags:
GA4 - Event - Signup Completed
GA4 - Config - Base Configuration
FB - Pixel - Page View
HTML - LiveChat Widget

Triggers:
Click - CTA Button
Submit - Contact Form
View - Pricing Page
Custom - signup_completed

Variables:
DL - user_id
JS - Current Timestamp
LT - Campaign Source Map
```

---

## Data Layer Patterns

### Basic Structure

```javascript
// Initialize (in <head> before GTM)
window.dataLayer = window.dataLayer || [];

// Push event
dataLayer.push({
  'event': 'event_name',
  'property1': 'value1',
  'property2': 'value2'
});
```

### 页面 Load Data

```javascript
// Set on page load (before GTM container)
window.dataLayer = window.dataLayer || [];
dataLayer.push({
  'pageType': 'product',
  'contentGroup': 'products',
  'user': {
    'loggedIn': true,
    'userId': '12345',
    'userType': 'premium'
  }
});
```

### Form Submission

```javascript
document.querySelector('#contact-form').addEventListener('submit', function() {
  dataLayer.push({
    'event': 'form_submitted',
    'formName': 'contact',
    'formLocation': 'footer'
  });
});
```

### Button Click

```javascript
document.querySelector('.cta-button').addEventListener('click', function() {
  dataLayer.push({
    'event': 'cta_clicked',
    'ctaText': this.innerText,
    'ctaLocation': 'hero'
  });
});
```

### E-commerce Events

```javascript
// Product view
dataLayer.push({ ecommerce: null }); // Clear previous
dataLayer.push({
  'event': 'view_item',
  'ecommerce': {
    'items': [{
      'item_id': 'SKU123',
      'item_name': 'Product Name',
      'price': 99.99,
      'item_category': 'Category',
      'quantity': 1
    }]
  }
});

// Add to cart
dataLayer.push({ ecommerce: null });
dataLayer.push({
  'event': 'add_to_cart',
  'ecommerce': {
    'items': [{
      'item_id': 'SKU123',
      'item_name': 'Product Name',
      'price': 99.99,
      'quantity': 1
    }]
  }
});

// Purchase
dataLayer.push({ ecommerce: null });
dataLayer.push({
  'event': 'purchase',
  'ecommerce': {
    'transaction_id': 'T12345',
    'value': 99.99,
    'currency': 'USD',
    'tax': 5.00,
    'shipping': 10.00,
    'items': [{
      'item_id': 'SKU123',
      'item_name': 'Product Name',
      'price': 99.99,
      'quantity': 1
    }]
  }
});
```

---

## 常见 Tag Configurations

### GA4 Configuration Tag

**Tag 类型:** Google 分析: GA4 Configuration

**Settings:**
- 衡量 ID: G-XXXXXXXX
- Send 页面浏览: Checked (for pageviews)
- User Properties: Add any user-level dimensions

**Trigger:** All Pages

### GA4 事件 Tag

**Tag 类型:** Google 分析: GA4 事件

**Settings:**
- Configuration Tag: Select your config tag
- 事件 Name: {{DL - event_name}} or hardcode
- 事件 Parameters: Add parameters from dataLayer

**Trigger:** Custom 事件 with 事件 name match

### Facebook Pixel - Base

**Tag 类型:** Custom HTML

```html
<script>
  !function(f,b,e,v,n,t,s)
  {if(f.fbq)return;n=f.fbq=function(){n.callMethod?
  n.callMethod.apply(n,arguments):n.queue.push(arguments)};
  if(!f._fbq)f._fbq=n;n.push=n;n.loaded=!0;n.version='2.0';
  n.queue=[];t=b.createElement(e);t.async=!0;
  t.src=v;s=b.getElementsByTagName(e)[0];
  s.parentNode.insertBefore(t,s)}(window, document,'script',
  'https://connect.facebook.net/en_US/fbevents.js');
  fbq('init', 'YOUR_PIXEL_ID');
  fbq('track', 'PageView');
</script>
```

**Trigger:** All Pages

### Facebook Pixel - 事件

**Tag 类型:** Custom HTML

```html
<script>
  fbq('track', 'Lead', {
    content_name: '{{DL - form_name}}'
  });
</script>
```

**Trigger:** Custom 事件 - form_submitted

---

## Preview and Debug

### Preview 模式

1. Click "Preview" in GTM
2. Enter site URL
3. GTM debug panel opens at bottom

**What to check:**
- Tags fired on this 事件
- Tags not fired (and why)
- Variables and their values
- Data layer contents

### Debug Tips

**Tag not firing:**
- Check trigger conditions
- Verify data layer push
- Check tag sequencing

**Wrong variable value:**
- Check data layer structure
- Verify variable path (nested objects)
- Check timing (data may not exist yet)

**Multiple firings:**
- Check trigger uniqueness
- Look for duplicate tags
- Check tag firing options

---

## Workspaces and Versioning

### Workspaces

Use workspaces for team collaboration:
- Default workspace for production
- Separate workspaces for large changes
- Merge when ready

### Version Management

**Best practices:**
- Name every version descriptively
- Add notes explaining changes
- Review changes before publish
- Keep production version noted

**Version notes 示例:**
```
v15: Added purchase conversion tracking
- New tag: GA4 - Event - Purchase
- New trigger: Custom Event - purchase
- New variables: DL - transaction_id, DL - value
- Tested: Chrome, Safari, Mobile
```

---

## Consent Management

### Consent 模式 Integration

```javascript
// Default state (before consent)
gtag('consent', 'default', {
  'analytics_storage': 'denied',
  'ad_storage': 'denied'
});

// Update on consent
function grantConsent() {
  gtag('consent', 'update', {
    'analytics_storage': 'granted',
    'ad_storage': 'granted'
  });
}
```

### GTM Consent 概览

1. Enable Consent 概览 in Admin
2. Configure consent for each tag
3. Tags respect consent state automatically

---

## Advanced Patterns

### Tag Sequencing

**配置 tags to fire in order:**
Tag Configuration > Advanced Settings > Tag Sequencing

**Use cases:**
- Config tag before 事件 tags
- Pixel initialization before 跟踪
- Cleanup after conversion

### Exception Handling

**Trigger exceptions** - Prevent tag from firing:
- Exclude certain pages
- Exclude internal traffic
- Exclude during 测试

### Custom JavaScript Variables

```javascript
// Get URL parameter
function() {
  var params = new URLSearchParams(window.location.search);
  return params.get('campaign') || '(not set)';
}

// Get cookie value
function() {
  var match = document.cookie.match('(^|;) ?user_id=([^;]*)(;|$)');
  return match ? match[2] : null;
}

// Get data from page
function() {
  var el = document.querySelector('.product-price');
  return el ? parseFloat(el.textContent.replace('$', '')) : 0;
}
```
