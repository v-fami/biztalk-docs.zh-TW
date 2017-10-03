---
title: "ReceiveLocation （ReceiveLocations 節點） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ReceiveLocation node [binding file]
ms.assetid: 706ec5b2-c26f-428a-ad56-1c01b34aa8f8
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f959dfc9aadfbf317d3843fb0ed174a2a0f22ea3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocation-receivelocations-node"></a>ReceiveLocation (ReceiveLocations 節點)
繫結檔案之 ReceiveLocations 節點的 ReceiveLocation 節點包含與該繫結檔案一起匯出之接收位置有關的特定資訊。  
  
## <a name="nodes-in-the-receivelocation-node"></a>ReceiveLocation 節點中的節點  
 下表列出可以為繫結檔案中的這個節點設定的屬性：  
  
|**名稱**|**節點類型**|**資料類型**|**說明**|**限制**|**註解**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|名稱|Attribute|xs:string|指定接收位置的名稱。|不需要|預設值：空白|  
|說明|元素|xs:string|指定接收位置的描述。|Required|預設值：空白|  
|位址|元素|xs:string|指定接收位置的位址。|Required|預設值：空白|  
|PublicAddress|元素|xs:string|指定接收位置的公用位址。|不需要|預設值：空白|  
|Primary|元素|xs:boolean|指定接收位置是否為主要的接收位置。|Required|預設值：無|  
|ReceiveLocationServiceWindowEnabled|元素|xs:boolean|指定是否啟用服務窗口。|Required|預設值：無<br /><br /> 指定**true**如果已啟用服務窗口; 否則指定**false。**|  
|ReceiveLocationFromTime|元素|xs:dateTime|指定服務窗口的開始時間。|Required|預設值：無|  
|ReceiveLocationToTime|元素|xs:dateTime|指定服務窗口的結束時間。|Required|預設值：無|  
|ReceiveLocationStartDateEnabled|元素|xs:boolean|指定是否啟用服務窗口的開始日期。|Required|預設值：無|  
|ReceiveLocationStartDate|元素|xs:dateTime|指定服務窗口的開始日期。|Required|預設值：無|  
|ReceiveLocationEndDateEnabled|元素|xs:boolean|指定是否啟用服務窗口的結束日期。|Required|預設值：無|  
|ReceiveLocationEndDate|元素|xs:dateTime|指定服務窗口的結束日期。|Required|預設值：無|  
|[ReceiveLocationTransportType](../core/receivelocationtransporttype-receivelocation-node.md)|記錄|ProtocolType (ComplexType)|指定此接收位置的傳輸類型。|Required|預設值：無|  
|ReceiveLocationTransportTypeData|元素|xs:string|指定此接收位置的傳輸類型屬性。|不需要|預設值：空白<br /><br /> 請參閱[整合式 BizTalk 配接器的組態屬性](../core/configuration-properties-for-integrated-biztalk-adapters.md)的配接器特定資訊可以儲存這個字串中的屬性。|  
|[接收管線](../core/receivepipeline-receivelocation-node.md)|記錄|PipelineRef (ComplexType)|指定此接收位置的接收管線。|Required|預設值：無|  
|ReceivePipelineData|元素|xs:string|指定用於此接收位置之接收管線特定的自訂組態。|Required|預設值：空白|  
|[傳送管線](../core/sendpipeline-receivelocation-node.md)|記錄|PipelineRef (ComplexType)|指定雙向接收位置的傳送管線。 **注意：**中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送管線的雙向接收指定的接收位置，而不是在接收埠。 除非繫結檔案另外指定，否則接收位置會從所屬的接收埠自動繼承傳送管線。|Required|預設值：無|  
|SendPipelineData|元素|xs:string|指定用於此接收位置之傳送管線特定的自訂組態。|Required|預設值：空白|  
|[EncryptionCert](../core/encryptioncert-receivelocation-node.md)|記錄|CertificateInfo (ComplexType)|指定與接收位置關聯的加密憑證。|不需要|預設值：無|  
|啟用|元素|xs:boolean|指定接收位置是否已啟用。|Required|預設值：無|  
|[ReceiveHandler](../core/receivehandler-receivelocation-node.md)|記錄|ReceiveHandlerRef (ComplexType)|指定要用於這個接收位置的接收處理常式。|不需要|預設值：無|