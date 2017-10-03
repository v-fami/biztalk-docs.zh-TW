---
title: "安裝 BizTalk Accelerator for SWIFT |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: documentation
ms.assetid: 8d492248-fde6-4fd8-be6b-e86ac7d0808b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94e28d5dac74bdbceb0fe4938810779d6ccb5c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="install-biztalk-accelerator-for-swift"></a>安裝 BizTalk Accelerator for SWIFT
安裝[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]BizTalk 伺服器上。 

\<！---上一個文字
-   [BizTalk Accelerator for SWIFT 的安裝指南](http://go.microsoft.com/fwlink/?LinkId=198120)    
-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]讀我檔案，位於 \Program Files\Microsoft BizTalk Accelerator for SWIFT \Documentation 資料夾。  
-->

## <a name="hardware-and-software-requirements"></a>硬體與軟體需求

最低硬體和軟體需求都相同[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。

|  |BizTalk 需求  |SQL 和作業系統需求 |  
|---------|---------|--------- | 
| [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)] | [BizTalk Server 2016 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) | **SQL Server 硬體和軟體需求**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server 硬體需求**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx) |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [硬體和軟體需求適用於 BizTalk Server 2013 和 2013 R2](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) |**SQL Server 硬體和軟體需求**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server 硬體需求**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx)  |

> [!TIP] 
> 列出的硬體需求是最小需求。 每個環境都不同，但您的環境極有可能需要更多需求。 請參閱 [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx) (安裝、調整大小、部署和維護 BizTalk Server 解決方案的建議)。 

## <a name="install-swift"></a>安裝 SWIFT

### <a name="before-you-begin"></a>開始之前

* 使用成員的帳戶登入 BizTalk Server 系統管理員群組。 
* 在您的 BizTalk Server 下載[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝程式正在`\BizTalk Accelerators`資料夾。
* BizTalk Server，必須先安裝，且必須執行 SQL Server。
* 無訊息安裝支援，但建議您不要因為所需的其他組態步驟的複雜度。
* A4SWIFT 安裝程式執行時永遠會`/InstallPlatform`引數。 如此一來，安裝程式一定會安裝 msvcr71.dll、 mfc71u.dll、 msvcp71.dll，與 atl71.dll，所需的 Visual Studio。 安裝程式會安裝這些 DLL 檔案至`%WINDIR%\System32`資料夾中，是否將 Dll 之前安裝與否。

### <a name="default-installation"></a>預設的安裝

1. 執行[!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe**以系統管理員身分。
2. 選取 [安裝]。
3. 輸入您的 [使用者名稱]、[組織] 和產品金鑰。 選取 **[下一步]**。
4. 閱讀授權合約，然後再選取**接受**。
5. 選取**完成**，然後選取**下一步**。
6. 檢閱**摘要**頁面。 若要進行任何變更，請選取**回**。

    若要啟用在系統重新開機之後自動登入的功能，請選取 [設定] 並輸入登入資訊。 這只會在安裝期間啟用。 安裝程式完成時，即會停用此設定。

    選取 [安裝]。
 
7. 選取**完成**時完成。 安裝程式產生的記錄檔是在暫存資料夾中，類似於： `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`。

> [!NOTE] 
> 如果**執行組態精靈**上完成安裝] 頁面上，選取了 [[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈會自動執行當您按一下**完成**。 


### <a name="custom-installation"></a>自訂安裝

1. 執行[!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe**以系統管理員身分。
2. 選取 [安裝]。
3. 輸入您的 [使用者名稱]、[組織] 和產品金鑰。 選取 **[下一步]**。
4. 閱讀授權合約，然後再選取**接受**。
5. 選取**自訂**，然後選取**下一步**。
6. 選取您的元件，然後選取**下一步**:

    | 選項 | 動作 |
    | --- | --- |
    | A4Swift 元件 | 所需的程序 （結構描述解析、 剖析、 驗證） SWIFT 訊息與 BizTalk Server |
    | 訊息修復和重新調整 | 安裝管線、 協調流程和執行階段結構描述。 傳訊、 修復和重新調整 SQL Server 中建立 A4SWIFT 資料庫。 |
    | 訊息修復和新送出 web 元件 | 訊息修復和新送出之建立驗證、 憑證安全性、 記錄和 BIC 查閱的 web 服務安裝元件。 |
    | 軟體開發套件 (SDK) | 適用於 Visual Studio 包含範例來源的程式碼、 工具套件，以及起始專案。 | 
    | BRE 部署公用程式 | 用於部署與已部署 SWIFT 訊息類型關聯之商務規則引擎 (BRE) 原則的公用程式。 |
    | 教學課程 | Iincludes 指示和範例開發 SWIFT 方案在 BizTalk Server 中。 |
    | 工具 | 包含 A4SWIFT 開發工具。 |
    | Source | 安裝範例 A4SWIFT 開發的原始程式碼。 |
    
6. 檢閱**摘要**頁面。 若要進行任何變更，請選取**回**。

    選取 [安裝]。
 
7. 選取**完成**時完成。 安裝程式產生的記錄檔是在暫存資料夾中，類似於： `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`。

> [!NOTE]
> 如果**執行組態精靈**上完成安裝] 頁面上，選取了 [[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]組態精靈會自動執行當您按一下**完成**。 

## <a name="next-steps"></a>後續的步驟
[設定 BizTalk Accelerator for SWIFT](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)