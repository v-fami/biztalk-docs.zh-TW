---
title: 建立及提交新訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating, messages
- submitting, messages
- messages, submitting
- messages, creating
ms.assetid: 88b7a2d3-44a4-44e4-ba8c-527c10290925
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42cd2a82fe0ecde75446e68f9f58e17f103e5efa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22209862"
---
# <a name="creating-and-submitting-a-new-message"></a>建立及提交新的訊息
本節說明如何提交新的訊息。 做為已修復的訊息，新的訊息必須驗證並核准訊息建立者以外的人。  
  
 若要提交新的訊息，您必須上傳到新的 SWIFT 訊息文件庫的您想要提交的訊息類型的訊息範本檔案。 您可以手動上傳的單一訊息的範本，或您可以上傳使用 FormPublish 工具的所有訊息範本。  
  
### <a name="to-upload-a-single-message-template-into-the-new-document-library"></a>若要將單一訊息範本上傳到新的文件庫  
  
1.  請參閱章節[表單產生器公用程式來產生 MT/MX InfoPath 表單](../../adapters-and-accelerators/accelerator-swift/form-generator-utility-to-generate-mt-mx-infopath-forms.md)如需相關指示。  
  
### <a name="to-create-and-submit-a-new-message"></a>若要建立並提交新的訊息  
  
1.  在 Internet Explorer 中，開啟 MRSR http://localhost/sites/bassite 您的網站。  
  
2.  按一下**文件**，然後按一下 **新 SWIFT 訊息**。  
  
3.  在 [新 SWIFT 訊息] 頁面中，按兩下包含您想要建立的訊息類型分類的名稱。  
  
4.  按一下您想要建立之訊息的表單範本。  
  
5.  在[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]2007年 視窗中的，在訊息形成，類型 （以星號說明） 的所有必要的欄位和任何選用的欄位，您想要使用的訊息資料。  
  
6.  若要查閱 BIC、 目前的角色： 建立窗格，請按一下**BIC 查閱**。  
  
7.  輸入的金融機構、 銀行代碼和國家/地區名稱，然後按一下**搜尋**。  
  
8.  從 [BIC 查閱] 窗格中，將複製到訊息形式的適當銀行代碼欄位的 BIC。  
  
9. 目前的角色： 建立窗格，請按一下**驗證**，然後按一下 **驗證訊息**。  
  
10. 在 [結果] 窗格的目前角色： 建立窗格，請判斷您需要在訊息中修正的錯誤。  
  
    > [!NOTE]
    >  如果您有固定的所有驗證錯誤訊息中，您只能提交新的訊息。  
  
11. 從標準工具列則位於視窗的頂端，按一下 **送出**。  
  
12. 在選取的憑證來簽署格式的數位簽章精靈頁面上，選取您想要使用的表單 （您為建立者建立的憑證） 的憑證。 按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。 按一下 **[下一步]**。  
  
    > [!NOTE]
    >  若要驗證數位簽章的有效性，請按一下**數位簽章**上**工具**功能表上，按一下您想要確認，然後再按一下數位簽章**檢視簽署表單**.  
  
13. 在輸入的註解的數位簽章精靈頁面上，按一下 **完成**。  
  
14. 在驗證表單的 數位簽章精靈頁面上，確認您所簽署的訊息正確。 按一下**檢視憑證**如果您想要確認您是否使用正確的簽章。 按一下**我已簽署前確認此內容**，然後按一下 **登**。  
  
15. 在 [確認數位簽章] 視窗中，按一下**關閉**。  
  
16. 在 [提交成功] 對話方塊中，按一下**確定**。  
  
17. 關閉[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]視窗。