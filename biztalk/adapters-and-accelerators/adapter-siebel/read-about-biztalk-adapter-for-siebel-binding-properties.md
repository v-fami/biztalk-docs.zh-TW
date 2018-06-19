---
title: 了解 BizTalk Adapter for Siebel 繫結屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- binding properties, setting
- binding properties, adapter
- how to, set binding properties
ms.assetid: 48c77a2d-091c-40e0-aaf3-dc2ec34c55f2
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3237be098ea19fc7ff35770ddcb38a10d1e85c1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224038"
---
# <a name="read-about-biztalk-adapter-for-siebel-binding-properties"></a>了解 BizTalk Adapter for Siebel 繫結屬性
[!INCLUDE[adaptersiebel_md](../../includes/adaptersiebel-md.md)]呈現數個可讓您控制其執行階段和設計階段行為的某些繫結屬性。 本節描述這些繫結屬性，並提供連結，這些主題說明如何設定它們。  
  
## <a name="the-siebel-adapter-binding-properties"></a>Siebel 配接器繫結屬性  
 下表顯示[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]繫結屬性依類別目錄分組。 類別目錄指的每個繫結屬性會出現提出以不同的應用程式設定配接器 （或） 繫結 對話方塊中的節點。  
  
|繫結屬性|類別目錄|Description|.NET 型別|  
|----------------------|--------------|-----------------|---------------|  
|EnableBizTalkCompatibilityMode|一般|指定是否應該載入 BizTalk 層次通道繫結項目。<br /><br /> 將此設**True**載入繫結項目。 否則，將此設**False**。<br /><br /> 使用從配接器時[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定屬性**True**。 當使用配接器從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，您都必須設定屬性**False**。|bool (System.Boolean)|  
|名稱|一般|指定所產生的檔案名稱[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來保存[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]用戶端類別。 [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]表單的檔案名稱的值附加 「 用戶端 」**名稱**屬性預設值是"SiebelBinding"; 針對此值，產生的檔案會命名為"SiebelBindingClient"。|string|  
|CloseTimeout|一般|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線關閉逾時。 預設值是 1 分鐘。|System.DateTime|  
|OpenTimeout|一般|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]連線開啟逾時。 預設值是 1 分鐘。|System.DateTime|  
|ReceiveTimeout|一般|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息接收逾時。 預設為 10 分鐘。|System.DateTime|  
|SendTimeout|一般|指定[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]訊息的傳送逾時。 預設值是 1 分鐘。|System.DateTime|  
|EnableConnectionPooling|連接|指定是否[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連接集區已啟用。 預設值是**true**，以指定的連接集區是否已啟用。|bool (System.Boolean)|  
|IdleConnectionTimeout|連接|指定[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]閒置連線逾時。 當連接閒置超過這個逾時的時間，會處置連接。 預設值是 1 分鐘。|System.DateTime|  
|MaxConnectionsPerSystem|連接|指定中的連接數目上限[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]連接集區。 預設為 5。 **MaxConnectionsPerSystem**是應用程式定義域中的靜態屬性。 這表示當您變更**MaxConnectionsPerSystem**應用程式定義域中的其中一個繫結執行個體，新值套用至從該應用程式網域內的所有繫結執行個體建立的所有物件。|int (System.Int32)|  
|EnablePerformanceCounters|診斷|指定是否[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]效能計數器和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]LOB 延遲效能計數器已啟用。 預設值是**true**; 啟用效能計數器。 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] LOB 延遲效能計數器會測量配接器在 Siebel 系統的呼叫所花費的總時間。|bool (System.Boolean)|  
|LogData|診斷|指定是否要擷取的追蹤中的商務資料。 預設值是**false**; 不會擷取商務資料。|bool (System.Boolean)|  
|AcceptCredentialsInUri|由不顯示[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]。|指定 Siebel 連線 URI 是否可包含針對 Siebel 系統的使用者認證。 預設值是**false**，表示停用連線 URI 中的使用者認證。 如果**AcceptCredentialsInUri**是**false**連線 URI 包含使用者認證和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]擲回例外狀況。 您可以設定**AcceptCredentialsInUri**至**true**如果您必須在 URI 中指定認證。 如需詳細資訊，請參閱[建立 Siebel 系統連接 URI](../../adapters-and-accelerators/adapter-siebel/create-the-siebel-system-connection-uri.md)。|bool (System.Boolean)|  
  
## <a name="how-do-i-set-siebel-binding-properties"></a>如何設定繫結屬性的 Siebel？  
 當您設定 Siebel 系統的連線時，您可以設定 Siebel 繫結屬性。 如需如何設定繫結屬性的資訊時您：  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]，請參閱[連接到 Visual Studio 中的 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/connect-to-the-siebel-system-in-visual-studio.md)。  
  
    > [!IMPORTANT]
    >  同時使用[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]或[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，如果您未指定類型字串的繫結屬性的值，且其預設值是 null，則該繫結屬性將無法使用繫結檔案 （XML 檔案） 或 app.config 檔案中分別。 您必須手動加入的繫結屬性和其值在繫結檔案或 app.config 檔案中，視需要。  
  
-   設定傳送埠或接收埠 （位置） 中[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案，請參閱[設定實體連接埠繫結使用連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。
  
-   使用程式設計方案中的 WCF 通道模型，請參閱[建立通道使用 Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md)。  
  
-   使用 WCF 服務模型程式設計方案中，請參閱[設定 WCF 用戶端在 Siebel 系統](../../adapters-and-accelerators/adapter-siebel/configure-a-wcf-client-for-a-siebel-system.md)。  
  
-   使用 WCF ServiceModel Metadata Utility Tool (svcutil.exe)，請參閱[for Siebel eBusiness 應用程式中使用 BizTalk Adapter ServiceModel Metadata Utility Tool](../../adapters-and-accelerators/adapter-siebel/use-the-servicemodel-metadata-utility-with-the-siebel-adapter.md)。  
  
## <a name="see-also"></a>另請參閱  
[開發 Siebel 應用程式](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)