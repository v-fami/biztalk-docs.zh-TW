---
title: "讀我檔案和 WCF LOB 配接器 SDK 中的隱私權 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 539a88f9-ce59-46e6-8c9a-418484eabff4
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b0e66bb7f13fd0a7cc39e983ac891708183662b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="readme-and-privacy-in-the-wcf-lob-adapter-sdk"></a>讀我檔案和 WCF LOB 配接器 SDK 中的隱私權
Windows Communication Foundation (WCF) 列的企業營運 (LOB) 配接器軟體開發套件 (SDK)  
  
## <a name="inside-the-sdk"></a>內部 SDK  
 下表顯示 WCF LOB 配接器 SDK 中的各種元件的內容\<安裝資料夾\>在執行安裝程式。  
  
|類型|位置|Description|  
|----------|--------------|-----------------|  
|執行階段|\<安裝資料夾\>\Bin\Microsoft.ServiceModel.Channels.dll<br /><br /> \<安裝資料夾\>\Bin\Microsoft.ServiceModel.Channels.Tools.MetadataSearchBrowse.dll|這些組件包含執行階段，包括工具內使用的主要表單元件的基底。|  
|工具|\<安裝資料夾\>\Tools\Microsoft.ServiceModel.Channels.Tools.PlugInPackage.dll<br /><br /> \<安裝資料夾\>\Tools\Microsoft.ServiceModel.Channels.Tools.BizTalkExtension.dll<br /><br /> \<安裝資料夾\>\Tools\Microsoft.ServiceModel.Channels.Wizards.dll|**新增配接器服務參考 Visual Studio 外掛程式**<br /><br /> （.NET 專案 [按一下滑鼠右鍵]，加入配接器服務參考）<br /><br /> **使用配接器服務 BizTalk 專案增益集**<br /><br /> （BizTalk 專案 [按一下滑鼠右鍵]，[新增]，新增產生的項目，使用配接器服務）<br /><br /> **WCF LOB 配接器開發精靈**<br /><br /> （檔案、 新的、 專案、 Visual C#、 WCF LOB 配接器）|  
|文件集|\<安裝資料夾\>\Documents\WCFLOBAdapterSDK.chm|此檔案包含概念性內容和此版本的受管理的參考內容。|  
|產品識別碼的檔案|\<安裝資料夾\>\Documents\pid.txt|此檔案包含 WCF LOB Adapter SDK 的產品識別碼。 在連絡 Microsoft 客戶服務及支援 (CSS) 時，請使用此產品識別碼做為參考。|  
|範例|\<安裝資料夾\>\Documents\Samples\ContosoAdapterSample.zip<br /><br /> \<安裝資料夾\>\Documents\Samples\EchoAdapterSample.zip|[Samples] 資料夾包含兩個範例配接器： Contoso 配接器和回應配接器。|  

## <a name="privacy"></a>隱私權
Microsoft 致力於保護使用者的隱私權。 當您建置配接器使用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，這可能會影響到使用者的隱私權。 例如，您的配接器可能會明確收集並傳送使用者認證或它可能會傳送和接收的特定業務系統中的機密資訊。 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]不會傳送任何資訊給 Microsoft 從您的應用程式除非使用者選擇將它傳送給我們。  
  
### <a name="windows-communication-foundation-privacy"></a>Windows Communication Foundation 隱私權  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是擴充功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，並因此依賴許多所提供的服務。 如需有關[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]隱私權，請參閱[Windows Communication Foundation 隱私權資訊](https://msdn.microsoft.com/library/ms733927.aspx)。  
  
### <a name="microsoft-wcf-lob-adapter-sdk-privacy"></a>Microsoft WCF LOB 配接器 SDK 隱私權  
 [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]是一種 API。 身為開發人員，您可以提供自訂的記錄與追蹤功能，以方便偵錯，微調，而且您稽核配接器中建立。 如果您提供這類功能，您必須考慮將記錄的資訊和如何資訊將會限制只有獲授權的個人存取的類型。 這可能包含下列項目：  
  
-   設定和維護適當存取控制清單 (Acl) 的記錄檔和追蹤檔案。  
  
-   寫入檔案之前，請篩選敏感性資料。  
  
-   寫入檔案之前，請加密機密資料。  