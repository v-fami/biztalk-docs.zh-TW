---
title: 一般疑難排解問答集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2f89d92-0a97-4017-8b8e-6afd8b20eaf4
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a47cfd0bc1d2de1ad044712c12b97260981e610
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37010647"
---
# <a name="general-troubleshooting-questions-and-answers"></a>一般疑難排解問答集
本主題有問題和解答，以便協助您解決問題的 BizTalk 對應工具。  
  
## <a name="how-do-i-specify-xslt-output-settings"></a>我該如何指定 XSLT 輸出設定？  
 您可以使用 BizTalk 對應工具加入或省略 XML 宣告，並控制輸出執行個體資料所使用的編碼方式。  
  
#### <a name="include-or-exclude-an-xml-declaration"></a>包含或排除 XML 宣告  
  
1.  在 [格線] 檢視中，按一下對應工具格線。 **屬性**視窗會顯示格線屬性。  
  
2.  中的下拉式清單**省略 XML 宣告**屬性中，選取**是**省略 XML 宣告，或選取**No**不表示省略 XML 宣告。  
  
#### <a name="set-encoding-for-output-instance-data"></a>設定編碼方式輸出執行個體資料  
  
1.  在 [格線] 檢視中，按一下對應工具格線。 **屬性**視窗會顯示格線屬性。  
  
2.  中的下拉式清單**XSLT 編碼**屬性中，選取您要字元集要用於輸出執行個體資料。  
  
## <a name="how-do-i-create-multipart-mappings"></a>我該如何建立多部分對應？  
 如果您有多個對應搭配使用時，您必須將它們結合在協調流程中，使用**轉換**圖形一起測試。 BizTalk 對應工具一次只能測試一個對應。  
  
## <a name="why-isnt-my-database-functoid-working"></a>為何我的資料庫運算質沒有作用？  
 資料庫運算質**資料庫尋查**並**值擷取程式 」** 不會直接傳回錯誤資訊; 相反地，它們擷取資訊並將其提供給**錯誤傳回**運算質，以供您的對應。 您可以使用**錯誤傳回**」 運算質進行錯誤偵測，在下列案例：  
  
- 當您的對應具有**資料庫尋查**或是**值擷取程式 」** 表現不如預期的運算質。 若要查看錯誤訊息，請暫時將運算質對應至輸出結構描述中的欄位。  
  
- 如果在資料庫作業失敗時，您的應用程式預期不同的訊息內容。 您可以使用**錯誤傳回**」 運算質偵測錯誤，並將錯誤訊息對應到替代的結構，如此下游應用程式可以反應以節制的方式。  
  
  若要避免只在執行階段偵測到的錯誤，請確定的第一個參數**錯誤傳回**運算質會輸出**資料庫尋查**運算質和不在任何其他運算質的輸出Database 類別目錄。  
  
  如需使用詳細資訊**錯誤傳回**運算質 （包括範例），請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="why-is-my-map-failing-when-calling-my-custom-functoid"></a>為何我的對應會在呼叫自訂運算質時失敗？  
 自訂運算質必須先安裝到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦上的全域組件快取 (GAC)，才能夠由對應叫用。 請確認包含自訂運算質的組件，已經獲得簽署並放置到 GAC 中。 另外，將組件複製到資料夾 “%BTSINSTALLPATH%\Developer Tools\Mapper Extensions” 中。  
  
 如需有關如何安裝至 GAC 的組件的詳細資訊，請參閱[組件安裝在 GAC 中](../core/assembly-installation-in-the-gac.md)。 若要檢視安裝在 GAC 中的組件，請瀏覽至您 [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] 安裝目錄的 Assembly 目錄。  
  
## <a name="see-also"></a>另請參閱  
 [地圖疑難排解](../core/troubleshooting-maps.md)