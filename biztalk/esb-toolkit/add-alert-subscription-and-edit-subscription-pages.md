---
title: 新增警示訂閱和編輯訂用帳戶頁面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad5e99f1-714e-458b-b5f0-85ac69be5335
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49bed9959b51439f21d625795a69804fd41d77ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290038"
---
# <a name="add-alert-subscription-and-edit-subscription-pages"></a>新增警示訂閱和編輯訂閱頁面
新增警示的訂用帳戶 和 編輯訂閱頁面如下。 它們不同於編輯訂閱 頁面會顯示的訂閱者識別碼 （目前的入口網站使用者的 Microsoft Windows 帳戶），且具有一組不同的按鈕。 圖 1 顯示 新增警示的訂用帳戶 和 編輯訂閱頁面。  
  
 ![新增警示編輯訂閱](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8 AddAlertEditSubscription")  
  
 **圖 1**  
  
 **ESB Management 入口網站加入警示訂閱和編輯訂閱頁面**  
  
 新增警示的訂用帳戶 和 編輯訂閱頁面允許您指定並修改下列項目：  
  
-   若要使用的訂用帳戶 （而不是您的 Microsoft Windows 帳戶電子郵件地址） 的自訂的電子郵件地址  
  
-   當您將會接受警示通知的時間週期  
  
-   事件，例如假期"黑色 out"期限  
  
-   入口網站不會傳送警示的重複間隔  
  
 您可以執行下列的新增警示訂閱和編輯訂閱頁面上：  
  
-   選取此核取方塊旁的 **自訂電子郵件**文字方塊，如果您想要用於您標準 Windows 帳戶的電子郵件地址，以不同的訂用帳戶的電子郵件地址，然後在文字方塊中輸入慣用的電子郵件地址。  
  
-   選取核取方塊，在頂端**排程**區段，如果您想要指定當入口網站應該會將警示傳送給您，，然後指定 之期間的開始和結束時間週期**開始時間**和**結束時間**下拉式清單。 外部這段期間發生的警示已排入佇列，並在指定期間內傳遞。  
  
-   輸入開始日期和結束日期**黑色逾時**是否有的週期，當您將無法接收和處理警示。 使用兩個日期的格式為 mm/dd/yyyy。  
  
-   選取**間隔**中**分鐘**期間的入口網站會比較產生的警示，並傳送一個多個執行個體的相同警示發生時。 這樣可避免建立大量的相同警示訊息快速所發生的錯誤。  
  
-   按一下**儲存**按鈕以建立或更新訂用帳戶。  
  
-   按一下**刪除**按鈕 （只適用於編輯訂閱 頁面），以刪除選取的訂用帳戶。  
  
-   按一下**取消**按鈕回到[警示檢視器 頁面](../esb-toolkit/alert-viewer-page.md)而無須建立或修改訂用帳戶。