---
title: 建立連接到 Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eeeab604-155e-4806-b77a-45319a3f8cc0
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ffdfdc8810024e331598211529f3a594e0169f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216574"
---
# <a name="create-a-connection-to-oracle-e-business-suite"></a>建立 Oracle E-business Suite 連線
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 Oracle E-business Suite 透過 WCF 端點位址的通訊。 在 WCF 中的端點位址識別服務的網路位置，以及通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]用以連接到 Oracle E-business Suite。 您必須指定連線 URI 時您：  
  
-   建立通道處理站或通道接聽程式使用 WCF 通道模型，或當您建立使用 WCF 服務模型的 WCF 用戶端或服務主機。  
  
-   建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。  
  
-   使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
-   使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]BizTalk Server 解決方案。  
  
-   您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  

## <a name="ways-to-connect-to-oracle"></a>如何連接到 Oracle  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援兩種方式建立基礎的 Oracle 資料庫的連接：  
  
-   **使用 tnsnames.ora**。 這種方法，連線配接器用戶端所提供的 URI 包含只輸入 tnsnames.ora 檔案中的網路服務名稱。 配接器從檔案中的網路服務名稱的項目中擷取連接參數，例如伺服器名稱、 服務名稱、 通訊埠編號，等等。 若要使用這種方法，執行 Oracle 用戶端的電腦必須設定要在 tnsnames.ora 檔案中包含之 Oracle 資料庫的網路服務名稱。  
  
    > [!IMPORTANT]
    >  由於 Oracle 用戶端的限制， **DataSourceName**中的參數 (net service name)[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)如果您不能包含超過 39 個字元。在交易中執行的作業。 因此，如果您在交易中執行作業，請確定**DataSourceName**參數值是否小於或等於 39 個字元。  
  
-   **不使用 tnsnames.ora**。 在這種方式，配接器用戶端會輸入直接在 連線 URI 中的連接參數。 這不需要網路服務名稱必須存在於用戶端電腦上 tnsnames.ora 檔案。 這個方法甚至不需要 tnsnames.ora 檔案存在於用戶端電腦上。  
  
    > [!IMPORTANT]
    >  如果您在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  

## <a name="in-this-section"></a>本節內容    
 下列主題描述如何建立之間的連線[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 Oracle E-business Suite:  
  
-   [設定 Oracle E-business Suite 配接器用戶端](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)： 使用 tnsnames.ora 以 cconfiguring （使用 tnsnames.ora 來建立連接時，才需要） 的 Oracle 用戶端的相關資訊  
  
-   [建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)： 連接屬性和 Oracle E-business Suite 連線 URI 的結構資訊
  
-   [連接到使用 Windows 驗證的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)： 連接到 Oracle 使用 Windows 驗證的相關資訊
  