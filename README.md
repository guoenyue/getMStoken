#微软的office 365有两套api都是通过azure来操作
  ##Azure AD1.0版本的使用 OpenID Connect 来访问web应用程序的地址：
  https://docs.microsoft.com/zh-cn/azure/active-directory/develop/active-directory-protocols-openid-connect-code
  
  ##Azure AD2.0版本的使用 OpenID Connect 来访问web应用程序的地址：
  https://developer.microsoft.com/zh-cn/graph/docs/concepts/auth_v2_user
  
#本例子中的文件功能说明
  ##本例子使用2.0版本的api请求资源
  ###index.html将进行登录跳转
  ###demo.html是跳转成功的返回页，此页面会得到token，通过请求头可以申请各类有权限的信息
  ###logout.html是退出登录的返回页
