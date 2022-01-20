# Discord-Login-As-Bot-Script
Fixed by me

# Script To login as bot:
## Note: this script can run without error but not work for some reason, if you're developer you can help me by find the error/missing part and open a pull request
```js
function botlogin(token) {
let dispatcher;
(webpackChunkdiscord_app.push([[''],{},e=>{m=[];for(let key in e.c){
if (e.c[key].exports) {
const module = e.c[key].exports.default || e.c[key].exports;
if (typeof(module) === 'object') {
if ('setToken' in module) {
module.setToken(token)
module.hideToken = () => {};
} // if ('setToken')
if ('dispatch' in module && '_subscriptions' in module) {
dispatcher = module;
} // if dispatch
if ('AnalyticsActionHandlers' in module) {
console.log('AnalyticsActionHandlers', module);
module.AnalyticsActionHandlers.handleTrack = (track) => {};
} // analystic
} else if (typeof(module) === 'function' && 'prototype' in module) {
const descriptors = Object.getOwnPropertyDescriptors(module.prototype);
if ('_discoveryFailed' in descriptors) {
const connect = module.prototype._connect;
module.prototype._connect = function(url) {
console.log('connect', url);
const oldHandleIdentify = this.handleIdentify;
this.handleIdentify = () => {
const identifyData = oldHandleIdentify();
identifyData.token = identifyData.token.split(' ').pop();
return identifyData;
};
const oldHandleDispatch = this._handleDispatch;
this._handleDispatch = function(data, type) {
if (type === 'READY') {
console.log(data);
data.user.bot = false;
data.user.email = 'None';
data.analytics_tokens = [];
data.connected_accounts = [];
data.consents = [];
data.experiments = [];
data.guild_experiments = [];
data.relationships = [];
data.user_guild_settings = [];
}
return oldHandleDispatch.call(this, data, type);
}
return connect.call(this, url);
};
}
}
}
console.log(dispatcher);
if (dispatcher) {
dispatcher.dispatch({
type: 'LOGIN_SUCCESS', token});
}
} // shit open of for (let c in e.c)
}]))
}
```
