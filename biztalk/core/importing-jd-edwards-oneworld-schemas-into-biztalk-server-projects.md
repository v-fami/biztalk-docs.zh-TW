---
title: "JD Edwards OneWorld 結構描述匯入至 BizTalk Server 專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generating schemas
- importing schemas
- schemas, generating
- schemas, importing into BizTalk Server projects
ms.assetid: 5bcaa276-8c76-4212-b373-de86e3008a69
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b0d7fec5acc991ae6c141f57297b7511281be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-jd-edwards-oneworld-schemas-into-biztalk-server-projects"></a>將 JD Edwards OneWorld 結構描述匯入至 BizTalk Server 專案
本主題討論瀏覽 JD Edwards OneWorld 伺服器，以及將結構描述匯入 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案。  
  
> [!NOTE]
>  您必須確定您已設定引數清單。 在協調流程中產生結構描述之前，您必須先更新 jdearglist.txt。 如需詳細資訊，請參閱[處理字串值](../core/handling-string-values1.md)。  
  
> [!NOTE]
>  每次變更 jdearglist 時，都必須為該商務物件重新產生結構描述。  
  
 在建立 JD Edwards OneWorld 邏輯系統後，您可以從 BizTalk Server 專案開啟 Microsoft 配接器精靈，以瀏覽 JD Edwards OneWorld。  
  
### <a name="to-import-schemas"></a>若要匯入結構描述  
  
1.  開啟 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
2.  以滑鼠右鍵按一下[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案，指向**新增**，然後選取**新增產生的項目**。  
  
3.  按一下**新增配接器**，然後選取**開啟**。  
  
4.  選取配接器，然後按一下 **下一步**。  
  
     JD. Edwards OneWorld XE 系統就會顯示在瀏覽器中。  
  
     ![](../core/media/jdedadapter-04-jdebrowse.gif "JDEdAdapter_04_JDEBrowse")  
  
     配接器精靈會顯示含有所有已定義系統的樹狀結構。 JD Edwards OneWorld 的模組太多，無法在一個長清單中顯示。 模組會依據名稱中的前三個字元分組。  
  
    -   階層的第一層是模組名稱所有三個字元的首碼清單。  
  
    -   第二層列示共用相同的三個字元首碼的所有模組。  
  
    -   最後一層列示屬於模組的商務功能。 當您展開服務圖示時，就能檢視它的作業。  
  
     展開作業會顯示輸入/輸出引數。  
  
     您可以展開輸入/輸出引數以檢視引數的資料類型。  
  
    > [!NOTE]
    >  如果伺服器物件定義變更，您必須重新產生結構描述以重新整理其中包含的資料。  
  
    > [!NOTE]
    >  如果您在產生結構描述後變更 jdearglist.txt，您必須重新產生結構描述以重新整理所包含的資料。 如需 jdearglist.txt 的相關資訊，請參閱[處理字串值](../core/handling-string-values1.md)。  
  
## <a name="generating-schemas"></a>產生結構描述  
 使用下列程序產生結構描述。  
  
#### <a name="to-generate-schemas"></a>產生結構描述  
  
1.  選取要匯入結構描述的項目。  
  
2.  按一下 （或拖曳） 將項目加入**傳輸**窗格 （針對 J.Edwards OneWorld 的輸入呼叫）。  
  
3.  按一下 **[確定]**。  
  
     針對所選 JD Edwards OneWorld 項目產生的結構描述就會匯入 BizTalk Server 專案。  
  
> [!NOTE]
>  使用 AddressBook (N0100041) 時，欄位名稱為**cActionCode**。 動作是 XML 檔案本身的一部分。 程式碼為：  
>   
>  --A 表示新增  
>   
>  --C 表示變更  
>   
>  --D 表示刪除  
>   
>  --I 表示查詢  
  
## <a name="see-also"></a>另請參閱  
 [建立 JD Edwards OneWorld 傳送處理常式](../core/creating-jd-edwards-oneworld-send-handlers.md)