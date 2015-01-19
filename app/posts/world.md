title: World is calling
date: 2015-01-19
published: True

Jacks are the gExperiment wihtout stigma

    :::python
    from urlparse import urljoin
    from flask import request
    from werkzeug.contrib.atom import AtomFeed
    
    
    def make_external(url):
        return urljoin(request.url_root, url)
    
    
    @app.route('/recent.atom')
    def recent_feed():
        feed = AtomFeed('Recent Articles',
                        feed_url=request.url, url=request.url_root)
        articles = Article.query.order_by(Article.pub_date.desc()) \
                          .limit(15).all()
        for article in articles:
            feed.add(article.title, unicode(article.rendered_text),
                     content_type='html',
                     author=article.author.name,
                     url=make_external(article.url),
                     updated=article.last_update,
                     published=article.published)
        return feed.get_response()