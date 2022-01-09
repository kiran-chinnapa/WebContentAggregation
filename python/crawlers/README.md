Crawler module spins up multiple spiders to get sitemaps and links for each company urls present 
in the grids defined in crawlers/crawlers/resources/prod_dmv_grids

Before execution make sure the linux server has the following settings for ulimit -n,
number of open files on the server.

ulimit -Hn 500000
ulimit -Sn 500000
fs.file-max = 2097152

reference: 
https://rtcamp.com/tutorials/linux/increase-open-files-limit/
https://www.cyberciti.biz/tips/linux-procfs-file-descriptors.html

Steps to execute extraction for Career_Page.grid 
log into aws-ec2 box

cd ~/kiran/crawlers/crawlers/spiders  \
python3 sitemap_pages_spider.py > sitemap.log 2>&1 & \
logs will be available in sitemap.log \
python3 url_extraction_spider.py > link_extractor.log 2>&1 & \
logs will be available in link_extractor.log

Steps to execute extraction for Job_Page.grid     
cd ~/kiran/crawlers/crawlers/spiders \
python3 jp_link_extractor.py > jp_link_extractor.log 2>&1 &     
logs will be available in jp_link_extractor.log

Steps to execute extraction for Jobs.grid     
cd ~/kiran/crawlers/crawlers/spiders \
python3 job_desc_extractor.py > job_desc_extractor.log 2>&1 &    
logs will be available in job_desc_extractor.log