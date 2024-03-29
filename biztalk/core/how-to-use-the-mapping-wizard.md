---
title: 如何使用對應精靈 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35b96cea-ead7-43de-8411-62d2c7d6620e
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b016eb0599924d4927868b6a19d3b57389e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257358"
---
# <a name="how-to-use-the-mapping-wizard"></a>如何使用對應精靈
此版本的「企業單一登入」包含對應精靈，可讓您輕鬆建立分支機構應用程式的對應。  
  
> [!NOTE]
>  您只能在 [外部 UserID] 是以 Windows 網域帳戶為基礎時使用對應精靈。  
  
### <a name="to-start-the-mapping-wizard"></a>啟動對應精靈  
  
1.  開啟 [企業單一登入]。  
  
2.  在 [領域] 窗格中，按一下**分支機構應用程式**。  
  
3.  以滑鼠右鍵按一下適當的分支機構應用程式。  
  
4.  按一下**建立對應**。 「對應精靈」隨即出現。  
  
5.  **歡迎使用對應精靈**  
  
    -   確認這是正確的分支機構應用程式，然後按一下 **下一步**。  
  
6.  **對應檔案選項**頁面  
  
    -   ENTSSO 會透過 XML 檔管理對應。 您可以選擇建立新檔案或使用現有檔案。  
  
7.  **檔案位置**頁面  
  
    -   選取要使用的檔案。  
  
    -   您必須按一下**驗證**驗證檔案，再繼續進行。 驗證狀態會顯示在**狀態**視窗。  
  
8.  **帳戶**頁面  
  
    -   選擇一或多個帳戶，以產生新的對應檔案，並按一下**驗證**。  
  
9. **外部使用者名稱**頁面  
  
    -   定義如何從 Windows 使用者帳戶產生外部使用者名稱。 當您在方塊中選取項目，您可以看到的名稱會出現在**範例**方塊。  
  
10. **產生**頁面  
  
    -   按一下**啟動**產生對應檔。 (在建立對應之前，您將能夠在下一頁檢視或視需要編輯檔案)。結果會顯示在下列三個視窗中。  
  
    -   **數目**中選取帳戶的對應是近似值，因為帳戶可能巢狀方式置於 其他帳戶。  
  
    -   按一下**檢視記錄檔**檢查任何錯誤或警告可能發生的。  
  
11. **選項**頁面  
  
    -   您的檔案已建立完成。 按一下**檢視/編輯對應檔案**視。  
  
    -   按一下**啟用對應**如果您想要自動啟用對應。 如果您未按一下此選項，則必須手動啟用對應。  
  
    -   按一下**設定密碼**以自動設定這些對應的密碼。  
  
12. **建立**頁面  
  
    -   建立對應之前, 按一下**檢視對應檔**視。  
  
    -   當您準備好時，按一下 **啟動**執行對應作業。 您的狀態會在下列三個方塊中顯示。  
  
    -   按一下**檢視記錄檔**檢查任何錯誤或警告可能發生的。  
  
13. **完成對應精靈畫面**  
  
14. 選取任何需要的選項，然後再按一下**完成**。