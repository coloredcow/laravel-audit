# Audit Logs for Laravel

A package to capture system activity in a Laravel application. Currently supports the following fields:
- IP of HTTP request,
- HTTP referer,
- a description of the action you want to audit.
- user id
- Other details like data and keys

## Installation

1. Run `composer require coloredcow/laravel-audit`
2. Add the `ColoredCow\LaravelAudit\AuditServiceProvider` to `config/app.php`
```
'providers' => [
    ColoredCow\LaravelAudit\AuditServiceProvider::class
];
```
3. Run `php artisan migrate`


## Usage

1. Use the `ColoredCow\LaravelAudit\Events\Auditable` trait in the events you want to audit. And add this to the contructor of the event.
```
$this->setAudit([
    'ip' => 'ip-of-user-here',
    'referer' => 'referer-address',
    'action' => 'description of event and action being audited'
]);
```
2. Use the `ColoredCow\LaravelAudit\Listeners\AuditActivities` listener to listen to the events to want to audit. Map it in the EventServiceProvider of your laravel application.

## Audit Facade

1. Add AuditFacade in your app to make a audit directly from the applications.

```
 AuditFacade::make(['action' => 'Audit Action']);
```
2. You can also overide other properties like ip, userid and descriptions.

```
 AuditFacade::make(['action' => 'Audit Action', 'ip' => 'My IP']);
```

