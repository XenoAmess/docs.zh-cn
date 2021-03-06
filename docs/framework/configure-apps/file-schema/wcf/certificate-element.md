---
title: '&lt;certificate&gt; 元素'
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 02444e66326bec10150ba52541aedd02ec7bb784
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749785"
---
# <a name="ltcertificategt-element"></a>&lt;certificate&gt; 元素
指定要用于为对等客户端的消息进行签名和加密的 X.509 证书。  
  
 \<system.ServiceModel>  
\<行为 >  
\<endpointBehaviors>  
\<行为 >  
\<clientCredentials>  
\<对等 >  
\<证书 >  
  
## <a name="syntax"></a>语法  
  
```xml  
<certificate findValue="String"   
  
storeLocation="LocalMachine/CurrentUser"  
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`findValue`|一个字符串，包含要在 X.509 证书存储中搜索的值。 此属性中包含的类型必须满足指定 `x509FindType` 的要求。 默认值为一个空字符串。|  
|`storeLocation`|指定客户端可用于验证对等方的证书的 X.509 证书存储的位置。 包括以下有效值：<br /><br /> -LocalMachine： 分配给本地计算机的证书存储。<br />-CurrentUser： 分配给当前用户的证书存储。<br /><br /> 默认值为 LocalMachine。|  
|`storeName`|指定要打开的 X.509 证书存储区的名称。 包括以下有效值：<br /><br /> -AddressBook： 其他用户证书存储区。<br />-AuthRoot： 证书存储第三方证书颁发机构 (Ca)。<br />-CertificateAuthority： 中间证书颁发机构 (Ca) 证书存储区。<br />-不允许： 证书吊销的证书存储。<br />-My： 个人证书的证书存储区。<br />-Root： 受信任的根证书颁发机构 (Ca) 证书存储区。<br />-TrustedPeople： 直接受信任的人和资源的证书存储区。<br />-TrustedPublisher： 直接受信任发布者证书存储区。<br /><br /> 默认值为 My。|  
|`X509FindType`|定义要执行的 X.509 搜索的类型。 包括以下有效值：<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-FindByTemplateName<br />-   FindByApplicationPolicy<br />-   FindByCertificatePolicy<br />-FindByExtension<br />-FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> `findValue` 属性中包含的类型必须满足指定 `X509FindType` 的要求。<br /><br /> 默认值为 FindBySubjectDistinguishedName。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|指定在向对等客户端进行身份验证时使用的凭据。|  
  
## <a name="remarks"></a>备注  
 此配置元素包含对对等网格中的邻居进行身份验证时使用的 X509Certificate2 实例。  
  
 有关对等编程的详细信息，请参阅[对等网络](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="example"></a>示例  
 下面的代码指定如何查找在对等方案中使用的证书。  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>  
 <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>  
 [使用证书](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [对等网络](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [对等通道消息身份验证](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [对等通道自定义身份验证](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [保护对等通道应用程序](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
