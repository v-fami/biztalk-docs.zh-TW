---
title: "設定 BizTalk Accelerator for SWIFT |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e34b0b2d-f563-468b-b6b9-536f0df96f52
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaa9812243ef7d5ff4bb8b902ac7aee48e54ab99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configure-biztalk-accelerator-for-swift"></a>設定 BizTalk Accelerator for SWIFT

設定[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]。 

當您安裝[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]，還有可讓您自動執行設定的核取方塊。 或者，您可以開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態，您的應用程式中所列。

本主題會示範如何設定[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]快速鍵，如何匯出或匯入組態，以及列出後設定步驟。

## <a name="configure-a4swift"></a>設定 A4SWIFT

1. 開啟 BizTalk Accelerator for SWIFT (A4SWIFT) 組態。
2. 選取**MCRR**。 MCRR 是您安裝時，才可以使用**Message Repair 和 New Submission**元件。
3. 當系統詢問**您想要建立新的資料庫群組**:

  * 選取此選項可建立新的群組中顯示**群組**窗格。 
  * 若要將現有的資料庫群組，取消核取此選項。

3. 如果您已安裝**Web 元件 Message Repair 和 New Submission**，然後選取**WebService**。
4. 選取要主控 A4SWIFT Web 服務的網站。 根據預設，會選取預設的網站。
5. 選取**套用組態**。
6. 在**摘要**，確認組態設定，然後按一下**設定**。 

    > [!TIP] 
    > 您可以視需要將組態設定儲存為 XML 檔案。

7. 選取**完成**時設定完成。

## <a name="export-or-import-a-configuration"></a>匯出或匯入組態
您可以將 A4SWIFT 的組態設定匯出至 XML 檔案。 接著可以設定另一個 A4SWIFT 安裝匯入這些設定。 

### <a name="export-the-configuration"></a>匯出設定

1. 開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯出組態**。
2. 在**存**，瀏覽至您要儲存組態檔中，輸入組態檔中，名稱的資料夾，然後**儲存**。
3. 已成功匯出時選取**確定**。

### <a name="import-a-configuration"></a>匯入組態
1. 開啟 Microsoft BizTalk Accelerator for SWIFT 組態，然後選取**匯入組態**。
2. 瀏覽至包含組態檔的資料夾，選取檔案，並選取**匯入**。

## <a name="post-configuration-steps"></a>組態後步驟

### <a name="add-users-to-the-a4swift-users-group"></a>將使用者新增至 A4SWIFT 使用者群組

設定之後[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef_md](../../includes/a4swift-currentversion-firstref-md.md)]，加入執行 BizTalkServerApplication 主控件執行個體的帳戶**A4SWIFT 使用者**群組 (*不* **A4SWIFT 管理員**群組)。 

**步驟**:

1. 開啟**服務**。 服務也會提供**伺服器管理員**，然後**工具**。 
2. 在清單中，尋找**BizTalk Service BizTalk Group: BizTalkServerApplication**。 
3. 雙選取，開啟其內容。
4. 在**登入** 索引標籤時，請注意，使用者帳戶列為**此帳戶**。
5. 開啟**本機使用者和群組**（在 電腦管理），然後尋找**A4SWIFT 使用者**群組。 將使用者帳戶加入至這個群組。

> [!TIP] 
> 主控件執行個體帳戶需要存取 BizTalk Server 資料庫主機訊息修復執行階段元件的這個群組成員資格。

### <a name="check-the-identity-of-the-application-pool"></a>檢查應用程式集區身分識別
A4SWIFT_MRSR web 服務裝載於 IIS 中的應用程式。 應用程式集區識別*無法*成網路服務。 應用程式集區身分識別變更為成員的本機或網域帳戶**A4SWIFT 使用者**群組。

**步驟**:

1. 開啟**Internet Information Services 管理員**。 IIS 管理員也會提供**伺服器管理員**，然後**工具**。 
2. 展開**Default Web Site**，然後選取 A4SWIFT_MRSR web 服務。 
3. 選取**基本設定**。 會列出應用程式集區的名稱。
4. 在左窗格中，選取**應用程式集區**，然後選取 應用程式集區。
5. 選取**進階設定**，並變更**識別**視。