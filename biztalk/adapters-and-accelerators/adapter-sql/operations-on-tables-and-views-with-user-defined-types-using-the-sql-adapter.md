---
title: 資料表和檢視表的作業使用 SQL 配接器的使用者定義型別 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4006bbe-91ca-4cd9-844d-5ed63142001f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dab9b8d008b9bb36fa5a09789b531ea9fbee113
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006423"
---
# <a name="operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter"></a>資料表和檢視表的作業使用 SQL 配接器的使用者定義型別
您可以使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]資料表或檢視表的使用者定義型別 (Udt) 的資料行上執行作業。 您可以使用標準的資料表作業 （Insert、 Update、 刪除，與 選取） 來讀取或寫入資料行中的資料，UDT 類型。 您也可以在這類資料表上執行預存程序和函式。 不過，您需要執行特定工作，您才能使用配接器，來操作 UDT 資料行的資料表。 一旦您執行這些工作，您可以使用配接器：  

-   執行 Insert、 Delete、 Update 和選取作業，如中所述[Insert、 update、 delete 或 select 作業使用 SQL 配接器的 BizTalk Server](../../adapters-and-accelerators/adapter-sql/insert-update-delete-or-select-using-the-sql-adapter-in-biztalk-server.md)。  

-   執行預存程序中所述[使用 BizTalk Server 的 SQL Server 中執行預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)。  

-   執行複合作業具有 UDT 資料行的資料表中所述[執行 SQL Server 上使用 BizTalk Server 的複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  

-   輪詢具有 UDT 資料行的資料表中所述[從 SQL Server 使用 BizTalk Server 接收輪詢為基礎的資料變更訊息](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md)。  

-   執行其他作業，如中所述[開發 BizTalk 應用程式](../../core/develop-your-biztalk-applications.md)。  

## <a name="considerations-while-performing-operations-on-tables-with-udts"></a>在執行使用 Udt 的資料表上的作業時的考量  
 您可以使用配接器具有 UDT 資料行的資料表上執行作業之前，您必須執行下列工作。  

- **產生作業使用的結構描述時 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  


  |                       UDT 類型                        |                                                                                                                                                                        組件的位置                                                                                                                                                                        |
  |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Udt 隨附於 SQL Server，例如地理位置  | -請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。<br />-請確定 SqlServerSpatial.dll 適用於 [System32] 資料夾。<br /><br /> 您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，然後選取**管理工具-基本**並**管理工具-完整**在**特徵選取**精靈頁面。 |
  | 並未隨附於 SQL Server，但使用者所定義的 Udt |                      請確定將個別的組件的 Udt 上有相同的位置[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]可執行檔的 devenv.exe。 可執行檔通常會在`<installation drive>:\Program Files\Microsoft Visual Studio <version>\Common7\IDE`。                      |


- **執行作業使用時 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]**  


  |                       UDT 類型                        |                                                                                                                                                                        組件的位置                                                                                                                                                                        |
  |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Udt 隨附於 SQL Server，例如地理位置  | -請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。<br />-請確定 SqlServerSpatial.dll 適用於 [System32] 資料夾。<br /><br /> 您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，然後選取**管理工具-基本**並**管理工具-完整**在**特徵選取**精靈頁面。 |
  | 並未隨附於 SQL Server，但使用者所定義的 Udt |                                     請確定 Udt 的個別組件都能使用 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安裝位置。 BizTalk server，這通常是\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。                                      |


- **執行作業使用時 [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]**  

  |UDT 類型|組件的位置|  
  |--------------|----------------------------|  
  |Udt 隨附於 SQL Server，例如地理位置|-請確定 Microsoft.SqlServer.Types.dll 加入至 GAC。<br />-請確定 SqlServerSpatial.dll 適用於 [System32] 資料夾。<br /><br /> 您可以在電腦上安裝這些 Dll，以執行 SQL Server 安裝程式，然後選取**管理工具-基本**並**管理工具-完整**在**特徵選取**精靈頁面。|  
  |並未隨附於 SQL Server，但使用者所定義的 Udt|請確定將個別的組件的 Udt 可用做為專案可執行檔，通常是專案的 \bin\Debug 資料夾下的所在位置。|  

  您已完成這些工作，您就全部設定為使用 Udt 的資料表上執行作業。  

## <a name="see-also"></a>另請參閱  
 [連接到 SAP 系統使用配接器](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)