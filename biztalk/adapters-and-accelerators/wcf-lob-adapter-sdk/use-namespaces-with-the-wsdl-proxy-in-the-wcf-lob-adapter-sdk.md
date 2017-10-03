---
title: "使用命名空間與 WCF LOB 配接器 SDK 中的 WSDL Proxy |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 781d20fa-83e3-42fa-866e-5650d5eb71a7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc85d47da81d2d7425c7db4aad90ea32389f7d84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk"></a>使用 WCF LOB 配接器 SDK 中的 WSDL Proxy 命名空間
[!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]產生 WSDL 和使用開發人員使用所提供的值為配接器的 proxy[!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)]或透過修改 SERVICENAMESPACE 私用變數的程式碼中指定及/或`Namespace`配接器的屬性。  
  
 結構描述類型與定義內的項目\<wsdl: types >\<結構描述 > 預設會使用 {OperationNamespace}。 如果特定的型別中設定覆寫的 TypeNamespace **TypeMetadata**物件，該命名空間用於複雜型別和 （或) 或元素定義。  
  
## <a name="impact-on-wsdl"></a>WSDL 的影響  
 下表顯示不同的命名空間中自訂配接器會如何影響對應的 WSDL。 在資料表中，~ {OperationNamespace} 是 URI; 的類別命名空間對應例如，如果 {OperationNamespace} 是 「 myscheme://a.b/c"，~ {OperationNamespace} 將 myscheme.a.b.c。  
  
|WSDL 建構|語法|  
|--------------------|------------|  
|WSDL targetNamespace<br /><br /> Xmlns:ts|{自訂}Adapter.Namespace|  
|\<porttype >|{配置}。 ~ {OperationNamespace}|  
|WSDL 輸入的訊息名稱|{配置}。 ~ {OperationNamespace} _ {OperationName} _InputMessage|  
|WSDL 輸出訊息名稱|{配置}。 ~ {OperationNamespace} _ {OperationName} _OutputMessage|  
|\<wsdl: types >\<結構描述 > targetNamespace|{配置}:// {OperationNamespace}|  
|\<項目 >\<complexType >|如果值不是 null 或空白，請使用 {TypeNamespace}。|  
  
## <a name="impact-on-proxy"></a>在 Proxy 上的影響  
 在 proxy 中的三個不同屬性受到命名空間：  
  
-   [**System.ServiceModel.ServiceContractAttribute**(名稱 ="{配置}。 ~ {OperationNamespace}"，Namespace="{Custom}Adapter.Namespace"]  
  
-   [**System.ServiceModel.MessageContractAttribute**(WrapperName ="DivideResponse"，WrapperNamespace ="{配置}:// {OperationNamespace}"，IsWrapped = true)]  
  
-   [**System.ServiceModel.MessageBodyMemberAttribute**(命名空間 ="{配置}:// {TypeNamespace}"，順序 = 0)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF LOB 配接器 SDK 開發最佳作法](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)