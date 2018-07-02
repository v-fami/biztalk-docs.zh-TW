---
title: 建立 Oracle E-business Suite 的連線 |Microsoft Docs
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
ms.openlocfilehash: c0da85f6c0968eb7257e980bdbd65a48fcf734f9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973303"
---
# <a name="create-a-connection-to-oracle-e-business-suite"></a>建立 Oracle E-business Suite 的連線
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。 因此，它可讓 Oracle E-business Suite 對透過 WCF 端點位址的通訊。 在 WCF 中的端點位址會識別服務的網路位置，而且通常表示做為統一資源識別元 (URI)。 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]用以連接到 Oracle E-business Suite。 您必須指定 URI 的連接時您：  
  
- 建立通道處理站或通道接聽程式使用 WCF 通道模型，或當您建立使用 WCF 服務模型的 WCF 用戶端或服務主機。  
  
- 建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
- 使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  
  
- 使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取訊息的結構描述從[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]BizTalk Server 解決方案。  
  
- 您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。  

## <a name="ways-to-connect-to-oracle"></a>如何連線至 Oracle  
 [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援兩種方式來建立基本的 Oracle 資料庫的連接：  
  
-   **使用 tnsnames.ora**。 這種方法，連線配接器用戶端所提供的 URI 會包含只輸入 tnsnames.ora 檔案中的 net 的服務名稱。 配接器會將連接參數，例如伺服器名稱、 服務名稱、 連接埠號碼，並依此類推，擷取檔案中的 net 的服務名稱項目。 若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。  
  
    > [!IMPORTANT]
    >  執行 Oracle 用戶端的限制，因為**DataSourceName**中的參數 （net 的服務名稱）[建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)不能包含超過 39 個字元，如果您是在交易中執行的作業。 因此，如果您要在交易中執行作業，請確定**DataSourceName**參數值是否小於或等於 39 個字元。  
  
-   **不使用 tnsnames.ora**。 在此方法中，配接器用戶端會輸入直接在 連線 URI 中的連接參數。 這不需要網路的服務名稱會出現在用戶端電腦上的 tnsnames.ora 檔案。 這種方法甚至不需要存在於用戶端電腦上的 tnsnames.ora 檔案。  
  
    > [!IMPORTANT]
    >  如果您要在交易中執行作業，則不支援這種連線模式。 這是因為 Oracle 用戶端的限制。  

## <a name="in-this-section"></a>本節內容    
 下列主題描述如何建立之間的連線[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]和 Oracle E-business Suite:  
  
-   [設定 Oracle 用戶端 E-business Suite 配接器](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-oracle-client-for-the-e-business-suite-adapter.md)： 使用 cconfiguring （使用 tnsnames.ora，以建立連線時，才需要） 的 Oracle 用戶端的 tnsnames.ora 的相關資訊  
  
-   [建立 Oracle E-business Suite 連線 URI](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md)： 連接屬性和 Oracle E-business Suite 連線 URI 的結構資訊
  
-   [連接到使用 Windows 驗證的 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-e-business-suite-using-windows-authentication.md)： 了解如何使用 Windows 驗證的 Oracle 連接
  