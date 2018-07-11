---
title: 如何：定义 Windows Communication Foundation 服务协定
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5e8abbf8c5f9b0696d90ccbee94c5d8f4dd8b1ec
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809220"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a>如何：定义 Windows Communication Foundation 服务协定
这是创建基本的 Windows Communication Foundation (WCF) 应用程序所需的六项任务的第一个。 有关全部六项任务的概述，请参阅[入门教程](../../../docs/framework/wcf/getting-started-tutorial.md)主题。  
  
 在创建 WCF 服务时，第一个任务是定义服务协定。 服务协定指定服务支持的操作。 可以将操作视为一个 Web 服务方法。 通过定义 C++、C# 或 Visual Basic (VB) 接口可创建协定。 接口中的每个方法都对应于特定的服务操作。 每个接口都必须将 <xref:System.ServiceModel.ServiceContractAttribute> 应用于它，而每个操作都必须将 <xref:System.ServiceModel.OperationContractAttribute> 特性应用于它。 如果接口中的一个方法具有 <xref:System.ServiceModel.ServiceContractAttribute> 特性而没有 <xref:System.ServiceModel.OperationContractAttribute> 特性，则服务不公开该方法。  
  
 在操作过程后面的示例中提供了用于此任务的代码。  
  
### <a name="to-define-a-service-contract"></a>定义服务协定  
  
1.  打开[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]以管理员身份中右键单击程序**启动**菜单并选择**以管理员身份运行**。  
  
2.  通过单击创建 WCF 服务库项目**文件**菜单并选择**新建**，**项目**。 在**新项目**对话框中，在对话框的左侧展开**Visual C#** 对于 C# 项目或**其他语言**然后**Visual Basic** Visual Basic 项目。 在所选的语言下选择**WCF**并将在对话框的中心部分上显示的项目模板列表。 选择**WCF 服务库**，并且在**名称**文本框中输入`GettingStartedLib`，并且在对话框底部的**解决方案名称**文本框中输入`GettingStarted`。  
  
3.  Visual Studio 将创建包含以下 3 个文件的项目：IService1.cs（或 IService1.vb）、Service1.cs（或 Service1.vb）和 App.config。IService1 文件包含默认的服务协定。  Service1 文件包含服务协定的默认实现。 App.config 文件包含 Visual Studio WCF 服务主机加载默认服务所需的配置。 有关 WCF 服务主机工具的详细信息，请参阅[WCF 服务主机 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)  
  
4.  打开 IService1.cs 或 IService1.vb 文件，删除命名空间声明内的代码，而留下命名空间声明。 在命名空间声明内，定义名为 `ICalculator` 的新接口，如下面的代码所示。  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     本协定定义了一个在线计算器。 注意，`ICalculator` 接口用 <xref:System.ServiceModel.ServiceContractAttribute> 特性标记。 此特性定义用于消除协定名称的歧义的命名空间。 每个计算器操作都用 <xref:System.ServiceModel.OperationContractAttribute> 特性标记。  
  
    > [!NOTE]
    >  使用特性给接口、成员或类进行批注时，可以从特性名称中去掉“Attribute”部分。 因此 <xref:System.ServiceModel.ServiceContractAttribute> 在 C# 中为 `[ServiceContract]`，在 Visual Basic 中为 `<ServiceContract>`。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [如何：实现服务协定](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [入门](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自承载](../../../docs/framework/wcf/samples/self-host.md)
