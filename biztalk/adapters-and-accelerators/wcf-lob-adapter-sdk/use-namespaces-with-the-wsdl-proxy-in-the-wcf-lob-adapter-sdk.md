---
title: 使用命名空間與 WCF LOB 配接器 SDK 中的 WSDL Proxy |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 781d20fa-83e3-42fa-866e-5650d5eb71a7
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc21b37ae80299bf5ddd78d1ca48331e1e369e78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965044"
---
# <a name="use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="7289a-102">使用 WCF LOB 配接器 SDK 中的 WSDL Proxy 命名空間</span><span class="sxs-lookup"><span data-stu-id="7289a-102">Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="7289a-103">[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]產生 WSDL 和使用開發人員使用所提供的值為配接器的 proxy[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]或透過修改 SERVICENAMESPACE 私用變數的程式碼中指定及/或`Namespace`配接器的屬性。</span><span class="sxs-lookup"><span data-stu-id="7289a-103">The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] generates WSDL and proxies for an adapter using values supplied by the developer using the [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] or specified in code through modification of the SERVICENAMESPACE private variable and/or the `Namespace` property of the adapter.</span></span>  
  
 <span data-ttu-id="7289a-104">結構描述類型與定義內的項目\<wsdl: types\>\<結構描述\>預設都會使用 {OperationNamespace}。</span><span class="sxs-lookup"><span data-stu-id="7289a-104">The schema types and elements defined within the \<wsdl:types\>\<schema\> use the {OperationNamespace} by default.</span></span> <span data-ttu-id="7289a-105">如果特定的型別中設定覆寫的 TypeNamespace **TypeMetadata**物件，該命名空間用於複雜型別和 （或) 或元素定義。</span><span class="sxs-lookup"><span data-stu-id="7289a-105">If a particular type has an overridden TypeNamespace set in the **TypeMetadata** object, that namespace is used for the complex type and/or or element definition.</span></span>  
  
## <a name="impact-on-wsdl"></a><span data-ttu-id="7289a-106">WSDL 的影響</span><span class="sxs-lookup"><span data-stu-id="7289a-106">Impact on WSDL</span></span>  
 <span data-ttu-id="7289a-107">下表顯示不同的命名空間中自訂配接器會如何影響對應的 WSDL。</span><span class="sxs-lookup"><span data-stu-id="7289a-107">The following table shows how the different namespaces in a custom adapter affect the corresponding WSDL.</span></span> <span data-ttu-id="7289a-108">在資料表中，~ {OperationNamespace} 是 URI; 的類別命名空間對應例如，如果 {OperationNamespace} 是 「 myscheme://a.b/c"，~ {OperationNamespace} 將 myscheme.a.b.c。</span><span class="sxs-lookup"><span data-stu-id="7289a-108">In the table, ~{OperationNamespace} is the class namespace mapping of a URI; for example, if {OperationNamespace} is "myscheme://a.b/c", ~{OperationNamespace} will be myscheme.a.b.c.</span></span>  
  
|<span data-ttu-id="7289a-109">WSDL 建構</span><span class="sxs-lookup"><span data-stu-id="7289a-109">WSDL Construct</span></span>|<span data-ttu-id="7289a-110">語法</span><span class="sxs-lookup"><span data-stu-id="7289a-110">Syntax</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="7289a-111">WSDL targetNamespace</span><span class="sxs-lookup"><span data-stu-id="7289a-111">WSDL targetNamespace,</span></span><br /><br /> <span data-ttu-id="7289a-112">Xmlns:ts</span><span class="sxs-lookup"><span data-stu-id="7289a-112">Xmlns:ts</span></span>|<span data-ttu-id="7289a-113">{自訂}Adapter.Namespace</span><span class="sxs-lookup"><span data-stu-id="7289a-113">{Custom}Adapter.Namespace</span></span>|  
|<span data-ttu-id="7289a-114">\<porttype\></span><span class="sxs-lookup"><span data-stu-id="7289a-114">\<wsdl:portType\></span></span>|<span data-ttu-id="7289a-115">{配置}。 ~ {OperationNamespace}</span><span class="sxs-lookup"><span data-stu-id="7289a-115">{scheme}.~{OperationNamespace}</span></span>|  
|<span data-ttu-id="7289a-116">WSDL 輸入的訊息名稱</span><span class="sxs-lookup"><span data-stu-id="7289a-116">WSDL Input Message Name</span></span>|<span data-ttu-id="7289a-117">{配置}。 ~ {OperationNamespace} _ {OperationName} _InputMessage</span><span class="sxs-lookup"><span data-stu-id="7289a-117">{scheme}.~{OperationNamespace}_{OperationName}_InputMessage</span></span>|  
|<span data-ttu-id="7289a-118">WSDL 輸出訊息名稱</span><span class="sxs-lookup"><span data-stu-id="7289a-118">WSDL Output Message Name</span></span>|<span data-ttu-id="7289a-119">{配置}。 ~ {OperationNamespace} _ {OperationName} _OutputMessage</span><span class="sxs-lookup"><span data-stu-id="7289a-119">{scheme}.~{OperationNamespace}_{OperationName}_OutputMessage</span></span>|  
|<span data-ttu-id="7289a-120">\<wsdl: types\>\<結構描述\>targetNamespace</span><span class="sxs-lookup"><span data-stu-id="7289a-120">\<wsdl:types\>\<schema\> targetNamespace</span></span>|<span data-ttu-id="7289a-121">{配置}:// {OperationNamespace}</span><span class="sxs-lookup"><span data-stu-id="7289a-121">{scheme}://{OperationNamespace}</span></span>|  
|<span data-ttu-id="7289a-122">\<項目\>\<complexType\></span><span class="sxs-lookup"><span data-stu-id="7289a-122">\<element\>\<complexType\></span></span>|<span data-ttu-id="7289a-123">如果值不是 null 或空白，請使用 {TypeNamespace}。</span><span class="sxs-lookup"><span data-stu-id="7289a-123">Use {TypeNamespace} if its value is not null or empty.</span></span>|  
  
## <a name="impact-on-proxy"></a><span data-ttu-id="7289a-124">在 Proxy 上的影響</span><span class="sxs-lookup"><span data-stu-id="7289a-124">Impact on Proxy</span></span>  
 <span data-ttu-id="7289a-125">在 proxy 中的三個不同屬性受到命名空間：</span><span class="sxs-lookup"><span data-stu-id="7289a-125">Three different attributes in the proxy are affected by namespaces:</span></span>  
  
-   <span data-ttu-id="7289a-126">[**System.ServiceModel.ServiceContractAttribute**(名稱 ="{配置}。 ~ {OperationNamespace}"，Namespace="{Custom}Adapter.Namespace"]</span><span class="sxs-lookup"><span data-stu-id="7289a-126">[**System.ServiceModel.ServiceContractAttribute**(Name="{scheme}.~{OperationNamespace}", Namespace="{Custom}Adapter.Namespace”]</span></span>  
  
-   <span data-ttu-id="7289a-127">[**System.ServiceModel.MessageContractAttribute**(WrapperName ="DivideResponse"，WrapperNamespace ="{配置}:// {OperationNamespace}"，IsWrapped = true)]</span><span class="sxs-lookup"><span data-stu-id="7289a-127">[**System.ServiceModel.MessageContractAttribute**(WrapperName="DivideResponse", WrapperNamespace="{scheme}://{OperationNamespace}", IsWrapped=true)]</span></span>  
  
-   <span data-ttu-id="7289a-128">[**System.ServiceModel.MessageBodyMemberAttribute**(命名空間 ="{配置}:// {TypeNamespace}"，順序 = 0)]</span><span class="sxs-lookup"><span data-stu-id="7289a-128">[**System.ServiceModel.MessageBodyMemberAttribute**(Namespace="{scheme}://{TypeNamespace}", Order=0)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7289a-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="7289a-129">See Also</span></span>  
 [<span data-ttu-id="7289a-130">使用 WCF LOB 配接器 SDK 開發最佳作法</span><span class="sxs-lookup"><span data-stu-id="7289a-130">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)