## 简要说明
整个过程中先明确微软各个工具之间的关系Azure AD是用来获取身份权限的一个工具，并且有两个版本（同时对应两套平台新建应用程序，和两套OAuth2.0的接口去申请身份认证【token,code,jit,asson_token...】)，然后通过一种方式获取到访问令牌之后再通过graph接口调取各种个人信息及其他接口资源（这个graph接口目前看到的所有文档都是v1.0系列）
所以要想成功的获取到所需要的资源正确的打开方式是：(AAD1.0||AAD2.0)&&(Graphx||Graph1.0)
***
本例子采用oAuch2.0(注意区分AAD2.0)并通过AAD2.0来获取token采用隐式授权的方式
官网手册地址：https://docs.microsoft.com/zh-cn/azure/active-directory/develop/active-directory-v2-protocols-implicit

微软的office 365有两套api都是通过azure来操作

Azure AD1.0版本的使用 OpenID Connect 来访问web应用程序的[地址](https://docs.microsoft.com/zh-cn/azure/active-directory/develop/active-directory-protocols-openid-connect-code)
  
  
Azure AD2.0版本的使用 OpenID Connect 来访问web应用程序的[地址](https://developer.microsoft.com/zh-cn/graph/docs/concepts/auth_v2_user)
  
  
## 本例子中的文件功能说明

    本例子使用2.0版本的api请求资源

*	index.html将进行登录跳转

*	demo.html是跳转成功的返回页，此页面会得到token，通过请求头可以申请各类有权限的信息

*	logout.html是退出登录的返回页

##  登出权限说明：
 https://login.microsoftonline.com/{tenant}/oauth2/v2.0/authorize?xxx
 
###   其中tenant
1.   可以是common【default】对登录无限制
2.   还可以是github.com【domain】限制域名
3.   还可以是organizations【仅拥有工作/学校帐户的用户】可以从 Azure AD 登录到应用程序。
4.   或者consumers【仅拥有 Microsoft 个人帐户的用户】可以登录到应用程序。
5.   还可以是租户在应用程序中的唯一标识。
    详细说明请查看[手册](https://docs.microsoft.com/zh-cn/azure/active-directory/develop/active-directory-v2-protocols-oidc)
