---
title: 產生和發佈 MT MX 表單在 SharePoint 網站上的 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4adf7117-11ad-4a8e-8d6a-fd78c5e496a3
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 492eda3b4bf3d3950c084bc9234b52b911b84a2b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980047"
---
# <a name="generating-and-publishing-mtmx-forms-on-the-sharepoint-site"></a>產生和發佈 MT/MX 表單在 SharePoint 網站上
**若要產生和發佈 MT/MX 表單在 SharePoint 網站上：**  

1. 下載表單產生器公用程式，並將它儲存在本機電腦上。  

2. 開啟**FormGenerator.sln**資料夾從上述下載並編譯解決方案。  

3. 在命令提示字元中，存取已編譯可執行檔 (FormGenerator.exe) 的資料夾。 例如，如果您已建立偵錯模式中的公用程式，存取 **...\bin\debug**資料夾。  

4. 輸入 FormGenerator.exe [-b] [-\<[否]。 範本資料夾路徑\>]  

    `<TemplateFolderPath> <DestinationFolderPath> <DocumentSchemaLocation> {[<SpaceSeparatedDocumentSchemaList>] | [-f <NameOfFileContainingSchemaList>]}`。 參數取代為新建立的資料夾名稱。  

5. 上述命令也會產生 MX 訊息修復所需的信封結構描述。  

6. 移至輸出資料夾\<DestinationFolderPath\>。 在  \<DestinationFolderPath\>，開啟您要產生表單的 InfoPath 表單範本的資料夾。 例如，如果您想要產生 MT103 InfoPath 表單，然後開啟 DestinationFolderPath 的 MT103 資料夾，然後開啟 TemplateDS.sln。  

7. 在 [方案總管] 中，按兩下**manifest.xsf**。 它會開啟將會需要一些時間才能取得開啟的 InfoPath 表單的設計檔案。  

   > [!NOTE]
   >  MX 訊息 manifest.xsf 可能需要 2 到 5 分鐘，才能取得開啟。  

8. 在 [manifest.xsf，移至**工具]-> [表單選項]-> 安全性和信任**功能表選項。 請檢查**完全信任**選項必須啟用權限。  

9. 選取 **簽章此表單範本**核取方塊。 按一下 **選取憑證**。 在這個中，選取您要登入表單的憑證。 按一下 [確定] 。  

10. 儲存**manifest.xsf**。  

11. 移至**檢視-> 設計工作**。 在設計工作] 窗格中，按一下 [**發佈表單範本**選項。  

12. 在 發行精靈 視窗中，選取**通往網路位置**然後按一下**下一步**。  

13. 在 表單範本的路徑和檔案名稱 文字方塊中輸入<strong>http://localhost/sites/BASSite/Templates/\<MessageType\>.xsn</strong>並輸入**\<MessageType\>** 表單範本中命名文字方塊，然後按一下**下一步**.  

14. 按 [下一步] 。  

15. 按一下 **發行並關閉**。  

16. 在 Internet Explorer 中，開啟 SharePoint 網站**http://localhost/sites/bassite/templates**。  

17. 指向 **\<MessageType\>**，按一下它，旁邊的向下箭號，然後按一下**編輯屬性**。  

18. 在範本中：\< MessageType\>視窗中的，在命名空間中：  

    - 如果您要產生 MT InfoPath 表單，輸入： **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMTxxx**  

    - 如果您要產生 MX InfoPath 表單，輸入： <strong>http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/EnvelopeMX_\<MessageName\></strong>  

       這有助於識別訊息執行個體與對應的範本。  

19. 按一下 **儲存並關閉**。
