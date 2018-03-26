---
title: 產生和發行 SharePoint 網站上的 MT MX Form |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c8bd8248a916d1e98571551a8561119b6377329
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="generating-and-publishing-mtmx-forms-on-the-sharepoint-site"></a>產生和發行 SharePoint 網站上的 MT/MX 表單
**若要產生並發佈在 SharePoint 網站上的 MT/MX 表單：**  
  
1.  下載表單產生器公用程式，並將它儲存在本機電腦上。  
  
2.  開啟**FormGenerator.sln**從資料夾下載的上方及編譯方案。  
  
3.  在命令提示字元中，存取已編譯的可執行檔 (FormGenerator.exe) 的資料夾。 例如，如果您已建立偵錯模式中的公用程式，存取**...\bin\debug**資料夾。  
  
4.  輸入 FormGenerator.exe [-b] [-\<[否]。 範本資料夾路徑的\>]  
  
     `<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`。 參數取代為新建立的資料夾名稱。  
  
5.  上述命令也會產生 MX 訊息修復所需的信封結構描述。  
  
6.  移至輸出資料夾\<DestinationFolderPath\>。 在\<DestinationFolderPath\>，開啟您要產生的表單的 InfoPath 表單範本的資料夾。 例如，如果您想要產生 MT103 InfoPath 表單，然後開啟 DestinationFolderPath MT103 資料夾，然後開啟 TemplateDS.sln。  
  
7.  在 [方案總管] 中，按兩下**manifest.xsf**。 它會開啟 InfoPath 表單將需要花一些時間才能取得開啟的設計檔案。  
  
    > [!NOTE]
    >  MX 訊息 manifest.xsf 可能需要取得開啟 2-5 分鐘。  
  
8.  在 manifest.xsf，移至**工具]-> [表單選項-> 安全性和信任**功能表選項。 請檢查**完全信任**選項必須啟用權限。  
  
9. 選取**簽署此表單範本**核取方塊。 按一下**選取憑證**。 在這個中，選取您要登入表單的憑證。 按一下 **[確定]**。  
  
10. 儲存**manifest.xsf**。  
  
11. 移至**檢視]-> [設計工作**。 在設計工作] 窗格中，按一下 [**發佈表單範本**選項。  
  
12. 在 [發行精靈] 視窗中，選取**至某個網路位置**按一下**下一步**。  
  
13. 在 [表單範本路徑和檔案名稱] 文字方塊中輸入**http://localhost/sites/BASSite/Templates/\<MessageType\>.xsn**和型別 **\<MessageType\>**表單範本中將文字方塊中，按一下**下一步**。  
  
14. 按一下 **[下一步]**。  
  
15. 按一下**發行並關閉**。  
  
16. 在 Internet Explorer 中，開啟您的 SharePoint 網站**http://localhost/sites/bassite/templates**。  
  
17. 指向 **\<MessageType\>**，按一下它，旁邊的向下箭頭，然後按一下**編輯內容**。  
  
18. 在範本：\< MessageType\>視窗中的，命名空間中：  
  
    -   如果您正在產生 MT InfoPath 表單，請輸入︰ **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**  
  
    -   如果您正在產生 MX InfoPath 表單，請輸入：  **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_ \<MessageName\>**  
  
         這有助於識別訊息執行個體與對應的範本。  
  
19. 按一下**儲存並關閉**。