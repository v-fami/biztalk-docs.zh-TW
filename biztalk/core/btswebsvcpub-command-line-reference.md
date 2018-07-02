---
title: BTSWebSvcPub 命令列參考 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5e19dd4d-9f2c-4a17-9437-8701e1c274fb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62df9b42a9bc709275c836ed2d670d017b217ef6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980439"
---
# <a name="btswebsvcpub-command-line-reference"></a>BTSWebSvcPub 命令列參照
本主題提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所附 BTSWebSvcPub 命令列工具的參考資訊。 您可以使用 BTSWebSvcPub 建立 Web 服務 (.asmx) 以便透過該 Web 服務發佈協調流程，如下所示：  
  
## <a name="usage"></a>使用方式  
 **BTSWebSvcPub 路徑名稱 [-位置：** *值* **] [-覆寫] [-匿名]**  
  
 **[-名稱：** *值* **] [-命名空間：** *值* **] [-TargetNamespace:** *值* **]**  
  
 **[-UnknownHeaders [** *+* **&#124;** *-* **]] [-單一登入 [** *+*  **&#124;** *-* **]] [-ParameterStyle:** *值***]**  
  
 **[-ConformanceClaims:** *值* **] [-ForceRequestResponse:** *值* **] [-ReceiveLocation]**  
  
 **[-ApplicationName:** *值* **]**  
  
## <a name="parameters"></a>參數  
  
|         參數         | 必要項 |                                                           描述                                                            |
|---------------------------|----------|----------------------------------------------------------------------------------------------------------------------------------|
|       **PathName**        |   是    |                    BizTalk 組件的路徑和檔案名稱 (\*.dll) 或 web 服務描述 (\*.xml) 檔案。                     |
|       **-位置**       |    否    |                                 要發佈的位置。 (語法:"http://host[: 連接埠] / 路徑 」)                                 |
|      **-覆寫**       |    否    |                                                  覆寫指定的位置。                                                   |
|      **匿名**       |    否    |                                              允許匿名存取 Web 服務。                                              |
|         **-名稱**         |    否    |                    要包含 Web 服務的解決方案和組件的名稱 (.sln 和 .dll 檔案)。                    |
|      **命名空間**       |    否    |                                             Web 服務代碼的預設命名空間。                                              |
|   **-目標命名空間**    |    否    |                        Web 服務的目標命名空間。 (範例:'<http://www.northwindtraders.com>')                        |
|    **-UnknownHeaders**    |    否    |                                                  支援未知 SOAP 標頭。                                                   |
|    **-SinglesSignon**     |    否    |                                  支援 SharePoint Portal Server 單一登入 SOAP 標頭。                                   |
|    **-ParameterStyle**    |    否    |                               訊息的 SoapParameterStyle:"Default"、"Bare"或"Wrapped"。                               |
|  **-ConfirmanceClaims**   |    否    |                              Web 服務互通性 (WSI) 主張:"None"或"BasicProfile1_1"。                              |
| **-ForceRequestResponse** |    否    |                                公開單向 BizTalk 作業，做為要求-回應的 Web 方法。                                |
|   **-ReceiveLocation**    |    否    |                                  在指定的 BizTalk 應用程式中建立接收位置。                                  |
|   **-ApplicationName**    |    否    | 要建立接收位置的 BizTalk 應用程式名稱。 若未指定，將使用預設的 BizTalk 應用程式。 |
  
## <a name="sample"></a>範例  
 BTSWebSvcPub.exe "MyAssembly.dll" -Location:<http://localhost/MyVdir>  
  
 -Overwrite  
  
## <a name="remarks"></a>備註  
 參數名稱不區分大小寫，而且可以縮寫。 參數值會區分大小寫。  
  
## <a name="see-also"></a>另請參閱  
 [如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)