---
title: 安裝 BizTalk Accelerator for HL7 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52347742-f858-47bb-bc73-1a6095ea9e8e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d20e2fa78d921c160b8dfe6b96c79c1b15d353e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004991"
---
# <a name="install-biztalk-accelerator-for-hl7"></a>安裝 BizTalk Accelerator for HL7

## <a name="hardware-and-software-requirements"></a>硬體與軟體需求

最低的硬體和軟體需求都相同[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。 


|                                                                                                                                                                   |                                                                                BizTalk 需求                                                                                 |                                                                                                                                                                                                                                                            SQL 和作業系統需求                                                                                                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                       [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]                                                        |             [BizTalk Server 2016 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)             |                                      **SQL Server 的硬體和軟體需求**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server 的硬體需求**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)                                      |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) | **SQL Server 的硬體和軟體需求**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server 的硬體需求**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx) |

> [!TIP]
> 列出的硬體需求是最小需求。 每個環境都不同，但您的環境極有可能需要更多需求。 請參閱[安裝、 調整大小、 部署和維護 BizTalk Server 解決方案的建議](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx)

## <a name="install-hl7"></a>安裝 HL7

### <a name="before-you-begin"></a>開始之前

* HL7 加速器安裝檔案位於`BizTalk Server <version>\BizTalk Accelerators`上[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]ISO，下載位置的網路共用，或您已下載的任一處[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]程式。
* 使用者安裝和設定[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]必須是 BizTalk 系統管理員群組的成員和 SQL Server 上的 Administrators 群組的成員位置[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]資料會儲存。
* 電腦與登入的使用者必須能夠存取網域主控站 (PDC)。 如果安裝程式無法存取 PDC，則安裝會失敗，而且將不會繼續。  
* BizTalk Server 應該包括方塊配接器，企業單一登入 (SSO) 的群組和執行階段從標準的 32 位元 biztalkserverapplication 主控件的基本元件安裝和設定。
* 讀取[已知問題的安裝](../../adapters-and-accelerators/accelerator-hl7/installation-known-issues.md)。
* [!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)] 適用於 Enterprise 和 Standard 版本。 下表顯示不同版本之間的相容性[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]和[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。  


  | [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 版本 | 相容的版本 [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] |
  |-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
  |                                      Enterprise Edition                                       |                                     Enterprise Edition                                      |
  |                                       Standard Edition                                        |                               Enterprise 或 Standard 版本                                |
  |                                       Developer Edition                                       |                                     Enterprise Edition                                      |

### <a name="default-installation"></a>預設安裝

1. 執行[!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)](A4HL7) **setup.exe**以系統管理員身分。 

   > [!TIP]
   >  開頭[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]和更新版本，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]安裝包含 32 位元安裝封裝和 64 位元安裝封裝。
   > 
   > 在 32 位元的電腦上，請只安裝 32 位元封裝。 在 64 位元電腦上安裝 32 位元**或**64 位元封裝。 64 位元封裝可讓配接器和管線在 32 位元和 64 位元模式中都能執行。  

2. 在 歡迎 頁面上選取**下一步**。  

3. 接受**授權合約**，然後選取**下一步**。  

4. 輸入您的使用者名稱和組織，然後選取**下一步**。  

5. 選取 [**典型**設定，然後按**下一步]**。  

6. **記錄的服務帳戶**頁面會自動提供給下列群組的記錄權限： 

   * BizTalk Server 系統管理員
   * BizTalk 應用程式使用者
   * BizTalk Server B2B 操作員
   * BizTalk Server 操作員

   選取 **[下一步]**。 

7. 檢閱摘要，然後選取**下一步**。  

8. 針對**目的地資料夾**，選取**下一步**以使用預設資料夾。 或者，選取**變更**選擇不同的安裝資料夾。 

9. 在 [**記錄資料庫資訊**，輸入下列命令，並選取**下一步]**。  


   |         使用         |                                                                                                                                                                                                                   以進行此動作                                                                                                                                                                                                                   |
   |--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | **資料庫伺服器名稱** |                                                                                                                             預設值是伺服器名稱。 <br/><br/>**請注意**的伺服器名稱預設為 BizTalkMgmtDb 資料庫所在之電腦的名稱。 您無法變更此值。                                                                                                                              |
   |  **HL7 資料庫名稱**   | 輸入包含資料的資料庫名稱您[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]解決方案，或接受預設設定，也就是**BTAHL7**。 <br/><br/>**請注意**您必須使用每個資料庫需求; ANSI-ASCII 字元集[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]不支援其他字元集。 |
   |   **測試連接**    |                                                                                                                                                                                              選取此選項，以確認您有 SQL Server 連線。                                                                                                                                                                                               |

    > [!NOTE]
    >  如果已選取的資料庫存在，則會出現訊息方塊。 按一下 [確定] 繼續進行。  

10. 選取 [安裝]。

11. 選取 **完成**時完成。  

    > [!TIP] 
    > 選取 **啟動的教學課程**安裝端對端教學課程。 

### <a name="custom-installation"></a>自訂安裝
1. 執行[!INCLUDE[btaBTAHL7NoNumber_md](../../includes/btabtahl7nonumber-md.md)](A4HL7) **setup.exe**以系統管理員身分。 

   > [!TIP]
   >  開頭[!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)]和更新版本，[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]安裝包含 32 位元安裝封裝和 64 位元安裝封裝。 
   > 
   > 在 32 位元的電腦上，請只安裝 32 位元封裝。 在 64 位元電腦上安裝 32 位元**或**64 位元封裝。 64 位元封裝可讓配接器和管線在 32 位元和 64 位元模式中都能執行。  

2. 在 歡迎 頁面上選取**下一步**。  

3. 接受**授權合約**，然後選取**下一步**。  

4. 輸入您的使用者名稱和密碼，然後選取**下一步**。  

5. 選取 [**自訂**，然後選取**下一步]**。  

6. 選取您想要安裝，然後選取的功能**下一步**。  


   |       功能        |      子功能       |                                                                                                   描述                                                                                                    | 一般安裝 | 自訂安裝 |
   |----------------------|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|----------------|
   |      **引擎**      |                        |                                 驗證、 處理並路由傳送訊息。<br /><br /> 您必須是 BizTalk Server 系統管理員群組的成員，才能安裝此功能。                                  |        ✓        |       ✓        |
   |      **引擎**      |   引擎元件    |                                      處理序[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]一般檔案和 XML 編碼訊息。                                      |        ✓        |       ✓        |
   |      **引擎**      |   輸出批次處理    |                                       建立和路由[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]批次格式的文件。                                        |        ✓        |       ✓        |
   |      **引擎**      |       管線        |                                      範例建置的管線您[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]解決方案。                                       |        ✓        |       ✓        |
   |     **配接器**      |                        |                                                                                    若要啟用端點連線的公用程式。                                                                                    |        ✓        |       ✓        |
   |     **配接器**      |          MLLP          |                          若要啟用 TCP 為主的連線，使用 MLLP 配接器[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]MLLP 通訊協定。                           |        ✓        |       ✓        |
   |     **配接器**      |     MLLP 測試工具     |                                                   測試模擬 MLLP 型傳送和接收透過 TCP 架構連線的用戶端應用程式的工具。                                                    |                 |                |
   |     **結構描述**      |                        |                                                                                HL7 V2 的選取項目。X 的一般檔案基礎 XSD 結構描述。                                                                                |        ✓        |       ✓        |
   |    **成品**     |                        |                                             使用工具[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]成品。                                              |                 |       ✓        |
   |    **成品**     |     協調流程      |                               範例協調流程，您可以使用來建置您[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]解決方案。                                |                 |       ✓        |
   | **其他元件** |     測試執行個體     |                           範例測試資料做為起點，您可以使用您[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]解決方案。                           |                 |                |
   | **其他元件** |           -            |                                                  中的其他元件[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]。                                                   |        ✓        |       ✓        |
   | **其他元件** | 組態總管 |                           您用來定義您的記錄資料存放區，應用程式設定合作對象的特定驗證、 標頭對應、 批次處理和通知需求。                            |        ✓        |       ✓        |
   | **其他元件** |          SDK           |                                    包含用於 HL7 2.xml 結構描述，公用程式，例如元件與成品所需的端對端教學課程和 MLLP 公用程式。                                     |        ✓        |       ✓        |
   | **其他元件** |   記錄架構    |                                       支援的記錄元件[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]事件。                                        |        ✓        |       ✓        |
   | **其他元件** |    入門專案     | 外掛程式[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，可讓[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]專案開發。 |        ✓        |       ✓        |


7. 在 [**記錄的服務帳戶**，輸入下列命令，並選取**下一步]**。  


   |     使用     |                              以進行此動作                              |
   |------------------|----------------------------------------------------------------------|
   | **帳戶名稱** | 輸入您想要用來啟動 「 記錄服務的帳戶名稱。 |
   |   **密碼**   |                 輸入此帳戶的密碼。                 |
   |    **網域**    |               輸入此帳戶的網域名稱。                |


8. 出現提示時**帳戶名稱已被授與登入為服務正確**，選取**確定**。  

9. 檢閱摘要，然後選取**下一步**。  

10. 針對**目的地資料夾**，選取**下一步**以使用預設資料夾。 或者，選取**變更**選擇不同的安裝資料夾。

11. 在 [**記錄資料庫資訊**頁面上，輸入下列命令，，然後選取**下一步]**。  


    |         使用         |                                                                                                                                                                                                                   以進行此動作                                                                                                                                                                                                                    |
    |--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | **資料庫伺服器名稱** |                                                                                                                              預設值是伺服器名稱。 <br/><br/>**請注意**的伺服器名稱預設為 BizTalkMgmtDb 資料庫所在之電腦的名稱。 您無法變更此值。                                                                                                                              |
    |  **HL7 資料庫名稱**   | 輸入包含資料的資料庫名稱您[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]解決方案，或接受預設設定; 也就是**BTAHL7**。 <br/><br/> **請注意**您必須使用每個資料庫需求; ANSI-ASCII 字元集[!INCLUDE[HL7_CurrentVersion_abbrev_md](../../includes/hl7-currentversion-abbrev-md.md)]不支援其他字元集。 |


12. 選取 [安裝]。  

13. 選取 **完成**時完成。  

    > [!TIP] 
    > 選取 **啟動的教學課程**安裝端對端教學課程。   

## <a name="next-steps"></a>後續的步驟
在一些教學課程逐步[開始使用 BizTalk Accelerator for HL7](../../adapters-and-accelerators/accelerator-hl7/get-started-with-the-biztalk-accelerator-for-hl7.md)。