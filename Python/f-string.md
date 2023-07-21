## print-f-string.py


```python
from rich import print
from datetime import datetime

print(f'')
print(f'## Basic:  [yellow]Formatting/Value/Output[/yellow]')

hdr = f'  Formatting          |  Value        |  Output '
print(f'')
num = 5
print(hdr)
print('='*len(hdr))
print(f'  {{num:0>2d}}          |  {num}            |  num = {num:0>2d}')

num = 5000000
print(f'  {{num:,}}             |  {num}      |  num = {num:,}')
print(f'  {{num:.2e}}           |  {num}      |  num = {num:.2e}')
print(f'')

pi = 3.141592654
print('  ("%%.2f" %% pi)       |  %.9f  |  pi = %.2f' % (pi, pi))
print('  "{{:.2f}}".format(pi) |  {}  |  pi = {:.2f}'.format(pi,pi))
print(f'  {{:.2f}}              |  {pi}  |  pi = {pi:.2f}')
print(f'  {{:+.2f}}             |  {pi}  |  pi = {pi:+.2f}')
print(f'  {{:.0f}}              |  {pi}  |  pi = {pi:.0f}')
print(f'')

num = 0.25
print(f'  {{num:.2%}}           |  {num}         |  num = {num:.2%}')
print(f'  {{num:>10}}           |  {num}         |  num = {num:>10}')
print(f'  {{num:<10}}           |  {num}         |  num = {num:<10}')
print(f'  {{num:^10}}           |  {num}         |  num = {num:^10}')
print(f'  {{num:0>9}}           |  {num}         |  num = {num:0>9}')
print(f'')

print("  '{{0}} >= {{1}}'.format('A','B')        |  {0} >= {1} ".format("A", "B"))
print("  '{{1}} <= {{0}}'.format('A','B')        |  {1} <= {0} ".format("A", "B"))
print(f'')
print("  '%%s loves %%s'%% ('cats','dogs')      |  %s loves %s" % ('cats', 'dogs'))
print("  '{{}} hates {{}}'.format('cats','dogs') |  {} hates {}".format('cats', 'dogs'))
print(f'')

now = datetime.now()
today = datetime.today()
utcnow = datetime.utcnow()
print(f'  {{now:%Y-%m-%d %H:%M}}                |  now()    = {now:%Y-%m-%d %H:%M}')
print(f'  {{today:%Y-%m-%d %H:%M}}              |  today()  = {today:%Y-%m-%d %H:%M}')
print(f'  {{utcnow:%Y-%m-%d %H:%M}}             |  utcnow() = {utcnow:%Y-%m-%d %H:%M}')
print(f'')

## defining formats
email_f = '  "Your email address is {email}"'.format
email_address = '_user@example.com_'
print(f'  email_f = "Your email address is {{email}}".format')
print(f'  email_address = "{email_address}"')
print(email_f(email=email_address))
print(f'')
```
