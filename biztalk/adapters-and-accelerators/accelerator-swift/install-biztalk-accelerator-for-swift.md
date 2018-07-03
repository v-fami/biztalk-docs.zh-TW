---
title: 安裝 BizTalk Accelerator for SWIFT |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- documentation
ms.assetid: 8d492248-fde6-4fd8-be6b-e86ac7d0808b
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cfd0ddfbdbe55480d249c01e68a0e571da63591
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006095"
---
# <a name="install-biztalk-accelerator-for-swift"></a>安裝 BizTalk Accelerator for SWIFT
安裝[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]BizTalk 伺服器上。 

\<！---之前的文字
- [BizTalk accelerator for SWIFT 的安裝指南](http://go.microsoft.com/fwlink/?LinkId=198120)    
- Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]讀我檔案，位於 \Program Files\Microsoft BizTalk Accelerator for SWIFT \Documentation 資料夾。  
  -->

## <a name="hardware-and-software-requirements"></a>硬體與軟體需求

最低的硬體和軟體需求都相同[!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]。


|                                                                                                                                                                   |                                                                                BizTalk 需求                                                                                 |                                                                                                                                                                                                                                                            SQL 和作業系統需求                                                                                                                                                                                                                                                            |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                       [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]                                                        |             [BizTalk Server 2016 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)             |                                      **SQL Server 的硬體和軟體需求**: <br/>[SQL Server 2016](https://msdn.microsoft.com/library/ms143506(v=sql.130).aspx)<br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/><br/>**Windows Server 的硬體需求**: <br/>[Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/server-basics)<br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)                                      |
| [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] <br/><br/> [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] 2013 | [BizTalk Server 2013 和 2013 R2 的硬體和軟體需求](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md) | **SQL Server 的硬體和軟體需求**: <br/>[SQL Server 2014](https://msdn.microsoft.com/library/ms143506(v=sql.120).aspx)<br/>[SQL Server 2012](https://msdn.microsoft.com/library/ms143506(v=sql.110).aspx)<br/>[SQL Server 2008 R2](https://msdn.microsoft.com/library/ms143506(v=sql.105).aspx)<br/><br/>**Windows Server 的硬體需求**: <br/>[Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx)<br/>[Windows Server 2008 R2](https://technet.microsoft.com/library/dd379511(v=ws.10).aspx) |

> [!TIP] 
> 列出的硬體需求是最小需求。 每個環境都不同，但您的環境極有可能需要更多需求。 請參閱 [Recommendations for Installing, Sizing, Deploying, and Maintaining a BizTalk Server Solution](http://social.technet.microsoft.com/wiki/contents/articles/666.recommendations-for-installing-sizing-deploying-and-maintaining-a-biztalk-server-solution.aspx) (安裝、調整大小、部署和維護 BizTalk Server 解決方案的建議)。 

## <a name="install-swift"></a>安裝 SWIFT

### <a name="before-you-begin"></a>開始之前

* 使用成員的帳戶登入 BizTalk Server 系統管理員群組。 
* 在您的 BizTalk Server 下載[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]安裝程式位於`\BizTalk Accelerators`資料夾。
* 必須安裝在 BizTalk Server 和 SQL Server 必須正在執行。
* 無訊息安裝支援，但建議您不要因為其他設定步驟所需的複雜性。
* A4SWIFT 安裝程式執行時永遠會`/InstallPlatform`引數。 如此一來，安裝程式一定會安裝 msvcr71.dll、 mfc71u.dll、 msvcp71.dll，與 atl71.dll，所需的 Visual Studio。 安裝程式會安裝這些 DLL 檔案`%WINDIR%\System32`資料夾中，是否將 Dll 到之前安裝與否。

### <a name="default-installation"></a>預設安裝

1. 執行[!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe**以系統管理員身分。
2. 選取 [安裝]。
3. 輸入您的 [使用者名稱]、[組織] 和產品金鑰。 選取 **[下一步]**。
4. 閱讀授權合約，然後按**接受**。
5. 選取 [ **Complete**，然後選取**下一步]**。
6. 檢閱**摘要**頁面。 若要進行任何變更，請選取**回**。

    若要啟用在系統重新開機之後自動登入的功能，請選取 [設定] 並輸入登入資訊。 這只會在安裝期間啟用。 安裝程式完成時，即會停用此設定。

    選取 [安裝]。

7. 選取 **完成**完成時。 安裝程式會產生記錄檔中的暫存資料夾，類似於： `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`。

> [!NOTE]
> 如果**執行組態精靈**上安裝已完成 頁面中，選取[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]當您按一下時自動執行組態精靈**完成**。 


### <a name="custom-installation"></a>自訂安裝

1. 執行[!INCLUDE[btaA4SWIFTNoVersion_md](../../includes/btaa4swiftnoversion-md.md)] **setup.exe**以系統管理員身分。
2. 選取 [安裝]。
3. 輸入您的 [使用者名稱]、[組織] 和產品金鑰。 選取 **[下一步]**。
4. 閱讀授權合約，然後按**接受**。
5. 選取 [**自訂**，然後選取**下一步]**。
6. 選取您的元件，然後選取**下一步**:


   |                     選項                      |                                                                      以進行此動作                                                                      |
   |------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                  A4Swift 元件                  |                          所需的程序 （結構描述解析、 剖析、 驗證） 與 BizTalk Server 的 SWIFT 訊息                          |
   |          訊息修復和重新調整           |    安裝管線、 協調流程和執行階段結構描述。 建立 A4SWIFT 資料庫在 SQL Server 中，傳訊、 修復和重新調整。     |
   | 訊息修復和新送出的 web 元件 | Message Repair 和 New Submission 建立驗證、 憑證安全性、 記錄和 BIC 查閱的 web 服務的安裝元件。 |
   |            軟體開發套件 (SDK)            |                                    適用於 Visual Studio 包含範例原始碼程式碼、 工具組，以及入門專案。                                    |
   |                BRE 部署公用程式                |               用於部署與已部署 SWIFT 訊息類型關聯之商務規則引擎 (BRE) 原則的公用程式。               |
   |                       教學課程                       |                                Iincludes 指示和範例來開發 BizTalk Server 中的 SWIFT 解決方案。                                 |
   |                        工具                         |                                                       包含 A4SWIFT 開發工具。                                                        |
   |                        來源                        |                                                 安裝範例 A4SWIFT 開發原始碼。                                                 |


7. 檢閱**摘要**頁面。 若要進行任何變更，請選取**回**。

    選取 [安裝]。

8. 選取 **完成**完成時。 安裝程式會產生記錄檔中的暫存資料夾，類似於： `C:\Users\username\AppData\Local\Setup(111016 xxxxxx).log`。

> [!NOTE]
> 如果**執行組態精靈**上安裝已完成 頁面中，選取[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]當您按一下時自動執行組態精靈**完成**。 

## <a name="next-steps"></a>後續的步驟
[設定 BizTalk Accelerator for SWIFT ](../../adapters-and-accelerators/accelerator-swift/configure-biztalk-accelerator-for-swift.md)