#自动化今日测试头条
pip 安装 Appium-Python-Client
从appium导入webdriver
导入单元测试



所需的大写字母 = {
    '平台名称': 'Android',
    'deviceName': '您的设备名称',
    'appPackage': 'com.example.yourapp', # 替换为你的应用包名
    'appActivity': '.MainActivity' # 替换为你的启动Activity
}

driver = webdriver.Remote('http://localhost:4723',desired_caps)

类 TestToutiao(unittest.TestCase):

    def（自身）：
        self.driver = webdriver.Remote('http://localhost:4723',desired_caps)

    def test_home_page(自身):
        #检查头条新闻是否能正常加载
        news_title = self.driver.find_element_by_id('news_title_id') # 替换为实际的新闻标题ID
        self.assertTrue(news_title.is_displayed())

        #切换不同分类
        category_button = self.driver.find_element_by_id('category_button_id') # 替换为实际的分类按钮ID
        类别_按钮.click()
        time.sleep(2) # 等待页面加载
        new_news_title = self.driver.find_element_by_id('news_title_id')
        self.assertNotEqual(new_title.text, new_news_title.text)

    def test_news_content_page(self):
        # 点击进入新闻详情页
        news_title = self.driver.find_element_by_id('news_title_id')
        news_title.click()
        时间.睡眠(2)

        # 检查文章内容是否加载
        Article_content = self.driver.find_element_by_id('article_content_id') # 替换为实际的文章内容ID
        self.assertTrue(article_content.is_displayed())

        #评论测试功能
        comment_button = self.driver.find_element_by_id('comment_button_id') # 替换为实际的评论按钮ID
        评论按钮.click()
        时间.睡眠(2)

    def test_comments_page(自我):
        # 发表评论
        input_box = self.driver.find_element_by_id('input_box_id') # 替换为实际的输入框ID
        input_box.send_keys('这是一条评论。')
        commit_button = self.driver.find_element_by_id('submit_button_id') # 替换为实际的提交按钮ID
        提交按钮.click()
        时间.睡眠(2)

        #检查评论是否成功发布
        my_comment = self.driver.find_element_by_xpath('//android.widget.TextView[@text="这是一条评论。"]')
        self.assertTrue(my_comment.is_displayed())

    def 拆解（自我）：
        self.driver.quit()

如果__ name __ == ' __ main __ ':
    单元测试.main ( )
