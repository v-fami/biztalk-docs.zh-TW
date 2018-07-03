---
title: 新增警示的訂用帳戶和編輯訂閱頁面 |Microsoft Docs
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
ms.openlocfilehash: 1b843bde8905d8b6803dda56a6370f70c934a610
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013447"
---
# <a name="add-alert-subscription-and-edit-subscription-pages"></a>新增警示的訂用帳戶和編輯訂閱頁面
新增警示的訂用帳戶 和 編輯訂用帳戶頁面很類似。 它們的差異在於 [編輯訂用帳戶] 頁面顯示的訂閱者識別碼 （目前的入口網站使用者的 Microsoft Windows 帳戶），並有一組不同的按鈕。 圖 1 顯示 新增警示的訂用帳戶 和 編輯訂用帳戶頁面。  

 ![新增警示編輯訂閱](../esb-toolkit/media/ch8-addalerteditsubscription.gif "Ch8 AddAlertEditSubscription")  

 **圖 1**  

 **ESB 管理入口網站新增警示的訂用帳戶 和 編輯訂用帳戶頁面**  

 新增警示的訂用帳戶 和 編輯訂用帳戶頁面可讓您指定，並修改下列：  

- 若要使用的訂用帳戶 （而不是您的 Microsoft Windows 帳戶電子郵件地址） 的自訂的電子郵件地址  

- 當您將會接受警示通知的時間週期  

- 事件，例如假期"黑色 out"期間  

- 透過入口網站不會傳送重複的警示間隔  

  您可以在 新增警示的訂用帳戶 和 編輯訂用帳戶頁面上：  

- 選取此核取方塊旁**自訂的電子郵件**文字方塊，如果您想要用於您標準 Windows 帳戶的電子郵件地址，以不同的訂用帳戶的電子郵件地址，然後在文字方塊中輸入慣用的電子郵件地址。  

- 選取頂端的核取方塊**排程**區段，如果您想要指定的期間，入口網站應該將警示傳送給您，並接著指定之期間的開始和結束時間時**開始時間**和**結束時間**下拉式清單。 這段期間外發生的警示已排入佇列，並傳遞指定的期間。  

- 輸入開始日期和結束日期**瑪莉亞期間**是否的期間，當您將無法接收和處理警示。 使用兩個日期的格式為 mm/dd/yyyy。  

- 選取 **間隔**中**分鐘**期間入口網站會比較引發的警示，並將只有一個傳送多個執行個體的相同警示發生時。 這可防止建立大量的相同警示訊息快速出現的錯誤。  

- 按一下 **儲存**按鈕來建立或更新訂用帳戶。  

- 按一下 **刪除**按鈕 （僅適用於 編輯訂用帳戶 頁面），以刪除選取的訂用帳戶。  

- 按一下 **取消**按鈕以返回[警示檢視器頁面](../esb-toolkit/alert-viewer-page.md)而不需要建立或修改訂用帳戶。
