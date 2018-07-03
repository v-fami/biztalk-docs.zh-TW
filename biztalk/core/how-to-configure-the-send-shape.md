---
title: 如何設定 「 傳送 」 圖形 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Send shape [Orchestration Designer], delivery notification
- send ports, delivery notifications
- configuring [Orchestration Designer], Send shapes
- Send shape [Orchestration Designer], configuring
- delivery notification
- messages, delivery notification
ms.assetid: 2cf4755b-1cfc-484e-bd9c-c9f3855af556
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bbfedd5067be1de443c20ce522cbe30f27395db1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36989959"
---
# <a name="how-to-configure-the-send-shape"></a>如何設定傳送圖形
![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")  
傳送圖形  
  
 若您預期收到您已送出訊息的間接或非同步回應 (不使用要求-回應連接埠)，則需要將訊息與目前正在執行的協調流程執行個體建立相互關聯，讓回應者能將回應送給正確的執行個體。 您可以套用下列的相互關聯集合來**傳送**圖形以先前初始化的相互關聯，或您可以套用初始相互關聯集。 如需詳細資訊，請參閱 <<c0> [ 協調流程中使用的相互關聯](../core/using-correlations-in-orchestrations.md)。  
  
### <a name="to-configure-a-send-shape"></a>設定傳送圖形  
  
1.  設定訊息和連接埠作業。  
  
    1.  在 [協調流程檢視] 視窗中，確認您的協調流程有為傳送的多部分訊息類型，定義訊息和連接埠作業。  
  
    2.  在 屬性 視窗中，選取 從傳送訊息**訊息**屬性下拉式清單。  
  
    3.  在 屬性 視窗中，選取 將訊息從傳送連接埠作業**連接埠作業**下拉式清單。  
  
         -或-  
  
         從傳送連接器拖曳到**傳送**圖形以將訊息傳送的連接埠通訊端。  
  
2.  指定相互關聯集來限制的訊息**傳送**」 圖形將傳送或初始化的相互關聯集合中的值。  
  
    1.  針對您想要使用的每個相互關聯集，檢查相互關聯集從下拉式清單上**沿用相互關聯集**屬性。  
  
    2.  用於每個相互關聯集您想要初始化，請檢查相互關聯集從下拉式清單上**初始相互關聯集**屬性。  
  
## <a name="delivery-notification"></a>傳遞通知  
 若要測試是否已經透過傳送埠成功傳送訊息，請完成下列步驟：  
  
1. 將您的「傳送」圖形放在非交易式、長時間執行或不可部分完成的範圍中。  
  
2. 在您的傳送埠，將 DeliveryNotification 屬性設定為**傳輸**。  
  
3. 將 Catch 處理常式新增到您的範圍，以處理 DeliveryFailureException。  
  
   > [!NOTE]
   >  如果 「 傳送 」 圖形包含不可部分完成的範圍內，DeliveryFailureException 依然可以攔截，但會需要使用交易類型設定為新增外部範圍圖形**長時間執行**或是**無**. 不可部分完成的範圍不能直接攔截例外狀況。  
  
   協調流程會在封閉式非不可部分完成之範圍的結尾，或是協調流程的結尾等待通知，以便接收通知。  
  
> [!NOTE]
>  這點僅適用於單向作業；如果在雙向 (要求 – 回應) 作業中失敗，即使沒有設定連接埠屬性，也會造成 SoapException (負值通知)。  
  
> [!NOTE]
>  直接繫結不支援傳遞通知。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理](../core/error-handling.md)