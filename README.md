to backup changes 
run (with erpnext-user priveleges)
bench --site smartb.dev backup 

then with root priveleges run
git add .
git commit -am "Server Backup Date"
git push
