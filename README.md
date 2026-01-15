# Youtube-Title-Scrape
Automatically update a YouTube video title using Google Apps Script. For example, this script changes your video title based on views count.

# How to Use?
1. Create a Google Apps Script Project
2. Enable YouTube Data API
- Click **Services (+)**
- Add **YouTube Data API v3**
3. Paste the Script
```bash
function updateView() {
  const videoID = 'YOUR_ID';
  const part = 'snippet,statistics';
  const param = {'id': videoID};
  const response = YouTube.Videos.list(part, param);
  const video = response.items[0];
  const views = video.statistics.viewCount;
  const title = 'This Video Have ' + views + ' Views';
  video.snippet.title = title;

  YouTube.Videos.update(video, part);
}
```
4. Replace **YOUR_ID** with your **YouTube video ID**