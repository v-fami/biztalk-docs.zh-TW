---
title: "部署 A4SWIFT 結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, A4SWIFT
- deploying, A4SWIFT schemas
- A4SWIFT, deploying schemas
- schemas, deploying
ms.assetid: a6aed2cd-3578-442e-ab1e-8284cc5f7b72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 331a21c64aa0130b3e110f1da6ca776f0b2c6a49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-a4swift-schemas"></a>部署 A4SWIFT 結構描述
您必須部署 SWIFT 訊息要交換的結構描述。  
  
 **摘要**  
  
 部署的下列結構描述：  
  
-   SWIFT 的基底 Types.xsd  
  
-   SWIFT 的常見資料 Types.xsd  
  
-   訊息類型，例如 MT103.xsd 特定結構描述  
  
### <a name="to-create-a-strong-named-swift-project"></a>若要建立強式名稱的 SWIFT 專案  
  
1.  在 Visual Studio 中，按一下 **檔案**，指向 **新增**，然後按一下 **專案**。  
  
2.  在 [新增專案] 對話方塊中**專案類型**窗格中，選取**BizTalk 專案**資料夾。  
  
3.  在**範本**窗格中，選取**空白 BizTalk Server 專案**。  
  
4.  在**名稱**方塊中，輸入您要針對專案名稱的名稱。  
  
5.  在**方案**方塊中，選取**建立新方案**。 在**位置**方塊中，輸入您要加入至結構描述專案之專案的位置。  
  
6.  按一下**確定**開啟新的專案。  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]將新專案加入方案總管 中，並在指定的資料夾中建立的專案資料夾和檔案。  
  
7.  啟動 Visual Studio 命令提示字元。  
  
8.  在 Visual Studio 命令提示字元中，瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft BizTalk Accelerator for SWIFT * *。  
  
9. 在命令提示字元中，輸入**sn – k key.snk**，然後按 ENTER 鍵。 請指出金鑰組已寫入至 key.snk [命令提示字元] 視窗中會顯示訊息。  
  
10. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**屬性**。  
  
11. 在左窗格中**屬性頁**對話方塊中，按一下 **組件**。  
  
12. 在右窗格中**屬性頁**對話方塊中，向下捲動至**強式名稱**區段中，按一下右邊的欄位**組件金鑰檔案**，然後按一下省略符號 （...） 按鈕。  
  
13. 在**組件金鑰檔案**對話方塊中，瀏覽至  **\<*磁碟機*>: \Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)]，按一下 **key.snk**，然後按一下 **開啟**。  
  
14. 在**屬性頁**對話方塊中，按一下 **確定**以儲存變更。  
  
### <a name="to-add-a-swift-schema"></a>若要加入 SWIFT 的結構描述  
  
1.  在 Visual Studio 的方案總管中開啟您的專案。  
  
2.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。  
  
3.  在**加入現有項目**對話方塊:\\**Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Base 結構描述**。 選取**SWIFT 基底 Types.xsd**和**SWIFT 常見資料 Types.xsd**結構描述，然後再按一下**新增**。  
  
4.  以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **加入現有項目**。  
  
5.  在**加入現有項目**對話方塊中，於**查看**下拉式清單方塊中，移至**\<磁碟機 >: \Program Files\Microsoft BizTalk Accelerator for SWIFT \<版本 > 訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本 > \Category n\MTxxx**。 選取訊息類型，結構描述執行個體**MT103.xsd**，然後按一下 **新增**。  
  
    > [!NOTE]
    >  方案總管 中所示，A4SWIFT 將加入您專案的結構描述。  
  
6.  在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**建置**。  
  
7.  在 [方案總管] 中，以滑鼠右鍵按一下專案名稱，然後**部署**。