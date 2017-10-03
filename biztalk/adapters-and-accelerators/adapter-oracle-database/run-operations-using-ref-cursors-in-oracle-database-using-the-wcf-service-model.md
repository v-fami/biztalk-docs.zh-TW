---
title: "使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, performing operations using REF CURSORS
- REF CURSORS, performing operations
ms.assetid: b4cb9ede-eae1-44d7-8ba5-7e1261ccfa3b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb527a4451388475ce69a5321d0d05616fc8afde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model"></a><span data-ttu-id="4e32e-102">使用 WCF 服務模型的 Oracle 資料庫中執行的作業使用 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4e32e-102">Run Operations Using REF CURSORS in Oracle Database using the WCF Service Model</span></span>
<span data-ttu-id="4e32e-103">REF CURSOR 是 Oracle 的 PL/SQL 資料類型，表示結果集的 Oracle 資料庫中的指標。</span><span class="sxs-lookup"><span data-stu-id="4e32e-103">A REF CURSOR is an Oracle PL/SQL data type that represents a pointer to a result set in the Oracle database.</span></span> <span data-ttu-id="4e32e-104">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援程序、 函數和封裝中的 REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-104">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports REF CURSOR parameters in procedures, functions, and packages.</span></span> <span data-ttu-id="4e32e-105">REF CURSOR 參數可以是強型別或弱型別取決於在程序或函式的宣告方式。</span><span class="sxs-lookup"><span data-stu-id="4e32e-105">REF CURSOR parameters can be strongly-typed or weakly-typed depending on how they are declared in the procedure or function.</span></span> <span data-ttu-id="4e32e-106">如需詳細說明的 REF CURSOR 參數都由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[REF CURSOR 的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)。下表摘要說明如何將 REF CURSOR 參數表示 WCF 服務模型中。</span><span class="sxs-lookup"><span data-stu-id="4e32e-106">For a detailed explanation of how REF CURSOR parameters are represented by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Message Schemas for REF CURSORS](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).The following table summarizes how REF CURSOR parameters are represented in the WCF service model.</span></span>  
  
|<span data-ttu-id="4e32e-107">參數方向</span><span class="sxs-lookup"><span data-stu-id="4e32e-107">Parameter Direction</span></span>|<span data-ttu-id="4e32e-108">強型別 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4e32e-108">Strongly-typed REF CURSOR</span></span>|<span data-ttu-id="4e32e-109">弱式類型的 REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4e32e-109">Weakly-typed REF CURSOR</span></span>|  
|-------------------------|--------------------------------|------------------------------|  
|<span data-ttu-id="4e32e-110">IN</span><span class="sxs-lookup"><span data-stu-id="4e32e-110">IN</span></span>|`string [PARAM_NAME]`<br /><br /> <span data-ttu-id="4e32e-111">字串，包含 PL/SQL 區塊。</span><span class="sxs-lookup"><span data-stu-id="4e32e-111">String that contains a PL/SQL block.</span></span> <span data-ttu-id="4e32e-112">執行 「 開啟的選取 」 陳述式或叫用函式或程序 PL/SQL 區塊必須傳回開啟的 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="4e32e-112">The PL/SQL block must return an opened REF CURSOR either by executing an "OPEN FOR SELECT" statement or by invoking a function or procedure.</span></span> <span data-ttu-id="4e32e-113">問號 （？） 指出傳回參數的 REF CURSOR 的位置。</span><span class="sxs-lookup"><span data-stu-id="4e32e-113">A question mark (?) indicates the position of the REF CURSOR that returns the parameter.</span></span> <span data-ttu-id="4e32e-114">例如，「 開始開啟？</span><span class="sxs-lookup"><span data-stu-id="4e32e-114">For example, "BEGIN OPEN ?</span></span> <span data-ttu-id="4e32e-115">選取 * 從 MY_TABLE;END"或"BEGIN MY_PROC (PARM1，？，PARM2);結束;"。</span><span class="sxs-lookup"><span data-stu-id="4e32e-115">FOR SELECT * FROM MY_TABLE; END", or "BEGIN MY_PROC(PARM1, ?, PARM2); END;".</span></span>|<span data-ttu-id="4e32e-116">相同強型別</span><span class="sxs-lookup"><span data-stu-id="4e32e-116">Same as strongly-typed</span></span>|  
|<span data-ttu-id="4e32e-117">OUT</span><span class="sxs-lookup"><span data-stu-id="4e32e-117">OUT</span></span>|`out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="4e32e-118">強類型的記錄組。</span><span class="sxs-lookup"><span data-stu-id="4e32e-118">A strongly-typed record set.</span></span>|`out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`<br /><br /> <span data-ttu-id="4e32e-119">弱型別泛型記錄集。</span><span class="sxs-lookup"><span data-stu-id="4e32e-119">A weakly-typed generic record set.</span></span>|  
|<span data-ttu-id="4e32e-120">IN OUT</span><span class="sxs-lookup"><span data-stu-id="4e32e-120">IN OUT</span></span>|<span data-ttu-id="4e32e-121">OUT REF CURSOR 參數會分為 IN 和 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-121">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="4e32e-122">IN 參數會附加"_IN 」 以便區別 OUT 參數的方法簽章中。</span><span class="sxs-lookup"><span data-stu-id="4e32e-122">The IN parameter is appended with "_IN" in the method signature to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="4e32e-123">OUT 參數會以強類型的資料錄集。</span><span class="sxs-lookup"><span data-stu-id="4e32e-123">The OUT parameter is represented by a strongly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [PROC_NS].[PARAM_NAME]RECORD[] [PARAM_NAME]`|<span data-ttu-id="4e32e-124">OUT REF CURSOR 參數會分為 IN 和 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-124">IN OUT REF CURSOR parameters are split into an IN and an OUT parameter.</span></span> <span data-ttu-id="4e32e-125">IN 參數會附加"_IN 」 以便區別 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-125">The IN parameter is appended with "_IN" to distinguish it from the OUT parameter.</span></span> <span data-ttu-id="4e32e-126">OUT 參數會以弱式類型的資料錄集。</span><span class="sxs-lookup"><span data-stu-id="4e32e-126">The OUT parameter is represented by a weakly-typed record set.</span></span><br /><br /> `string [PARAM_NAME]_IN`<br /><br /> `out [GENERIC_NS].GenRecordRow[] [PARAM_NAME]`|  
  
 <span data-ttu-id="4e32e-127">[PARAM_NAME] = Oracle 資料庫上的函式或程序定義中的參數名稱例如，MYREFCURSOR。</span><span class="sxs-lookup"><span data-stu-id="4e32e-127">[PARAM_NAME] = the name of the parameter in the function or procedure definition on the Oracle database; for example, MYREFCURSOR.</span></span>  
  
 <span data-ttu-id="4e32e-128">[PROC_NS] = 可以包含參數的封裝、 程序或函式; 產生唯一的命名空間例如，"microsoft.lobservices.oracledb._2007._03.SCOTT。Package.ACCOUNT_PKG。GET_ACTIVITY"。</span><span class="sxs-lookup"><span data-stu-id="4e32e-128">[PROC_NS] = The unique namespace generated to contain parameters of the package, procedure, or function; for example, "microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY".</span></span>  
  
 <span data-ttu-id="4e32e-129">[GENERIC_NS] = 命名空間中定義的是一般的資料錄集，「 microsoft.lobservices.oracledb._2007._03"。</span><span class="sxs-lookup"><span data-stu-id="4e32e-129">[GENERIC_NS] = The namespace in which the generic record set is defined, "microsoft.lobservices.oracledb._2007._03".</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="4e32e-130">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="4e32e-130">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="4e32e-131">本主題中的範例使用 Oracle SCOTT/封裝/ACCOUNT_PKG 封裝。</span><span class="sxs-lookup"><span data-stu-id="4e32e-131">The examples in this topic use the /SCOTT/Package/ACCOUNT_PKG Oracle PACKAGE.</span></span> <span data-ttu-id="4e32e-132">從 ACCOUNT_PKG 使用下列程序：</span><span class="sxs-lookup"><span data-stu-id="4e32e-132">The following procedure is used from ACCOUNT_PKG:</span></span>  
  
```  
PROCEDURE get_activity(inrecs IN SYS_REFCURSOR, status OUT NUMBER, inoutrecs IN OUT activity_ref_type, outrecs OUT SYS_REFCURSOR);  
```  
  
 <span data-ttu-id="4e32e-133">指令碼來產生這個封裝所提供的 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="4e32e-133">A script to generate this package is supplied with the SDK samples.</span></span> <span data-ttu-id="4e32e-134">如需 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="4e32e-134">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="ref-cursor-parameters-in-the-wcf-service-model"></a><span data-ttu-id="4e32e-135">WCF 服務模型中的 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="4e32e-135">REF CURSOR Parameters in the WCF Service Model</span></span>  
 <span data-ttu-id="4e32e-136">下列範例顯示類別和 /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序產生 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4e32e-136">The following examples show the classes and WCF client generated for the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure.</span></span> <span data-ttu-id="4e32e-137">此程序具有弱式型別的 IN 和 OUT REF CURSOR 參數和強型別在 OUT REF CURSOR 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-137">This procedure has weakly-typed IN and OUT REF CURSOR parameters and a strongly-typed IN OUT REF CURSOR parameter.</span></span>  
  
 <span data-ttu-id="4e32e-138">以下是產生 WCF 用戶端來叫用 GET_ACTIVITY 中方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="4e32e-138">Here is the signature of the method that is generated in the WCF client to invoke GET_ACTIVITY.</span></span>  
  
```  
public System.Nullable<decimal> GET_ACTIVITY(string INRECS, string INOUTRECS_IN, out microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY.INOUTRECSRECORD[] INOUTRECS, out microsoft.lobservices.oracledb._2007._03.GenRecordRow[] OUTRECS);  
```  
  
 <span data-ttu-id="4e32e-139">在**GET_ACTIVITY**方法中，在 OUT 參數 INOUTRECS 會分成兩個參數：</span><span class="sxs-lookup"><span data-stu-id="4e32e-139">In the **GET_ACTIVITY** method, the IN OUT parameter INOUTRECS is split into two parameters:</span></span>  
  
-   <span data-ttu-id="4e32e-140">INOUTRECS_IN 是表示在 REF CURSOR 參數的字串。</span><span class="sxs-lookup"><span data-stu-id="4e32e-140">INOUTRECS_IN is a string that represents an IN REF CURSOR parameter.</span></span>  
  
-   <span data-ttu-id="4e32e-141">INOUTRECS 是表示出 REF CURSOR 參數的強型別記錄集。</span><span class="sxs-lookup"><span data-stu-id="4e32e-141">INOUTRECS is a strongly-typed record set that represents an OUT REF CURSOR parameter.</span></span>  
  
 <span data-ttu-id="4e32e-142">弱式型別的 OUT 參數，OUTRECS，被以泛型資料錄集。</span><span class="sxs-lookup"><span data-stu-id="4e32e-142">The weakly-typed OUT parameter, OUTRECS, is represented as a generic record set.</span></span> <span data-ttu-id="4e32e-143">弱型別參數，INRECS，會以字串表示。</span><span class="sxs-lookup"><span data-stu-id="4e32e-143">The weakly-typed IN parameter, INRECS, is represented as a string.</span></span>  
  
### <a name="strongly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="4e32e-144">強型別出 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="4e32e-144">Strongly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="4e32e-145">強型別 （或在 OUT） REF CURSOR 參數會產生唯一的命名空間會根據結構描述、 套件和程序或函式中使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e32e-145">Strongly-typed OUT (or IN OUT) REF CURSOR parameters are generated in a unique namespace based on the SCHEMA, PACKAGE, and name of the procedure or function in which they are used.</span></span> <span data-ttu-id="4e32e-146">/SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY 程序，此命名空間是`microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`。</span><span class="sxs-lookup"><span data-stu-id="4e32e-146">For the /SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY procedure, this namespace is `microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY`.</span></span> <span data-ttu-id="4e32e-147">類別名稱的正確方式是將附加的 「 記錄 」 的參數名稱和類別由代表 Oracle 欄位的屬性構成。</span><span class="sxs-lookup"><span data-stu-id="4e32e-147">The class name is formed by appending the name of the parameter with "RECORD" and the class is composed of properties that represent the Oracle fields.</span></span> <span data-ttu-id="4e32e-148">以下顯示類別，表示為 INOUTRECS REF CURSOR 參數產生的強型別記錄的一部分。</span><span class="sxs-lookup"><span data-stu-id="4e32e-148">The following shows a part of the class that represents the strongly-typed records generated for the INOUTRECS REF CURSOR parameter.</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class INOUTRECSRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        ...  
  
        private System.Nullable<decimal> TIDField;  
  
        ...  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public System.Nullable<decimal> TID {  
            get {  
                return this.TIDField;  
            }  
            set {  
                this.TIDField = value;  
            }  
        }  
  
        ...  
  
    }  
}  
```  
  
### <a name="weakly-typed-out-ref-cursor-parameters"></a><span data-ttu-id="4e32e-149">弱型別出 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="4e32e-149">Weakly-Typed OUT REF CURSOR Parameters</span></span>  
 <span data-ttu-id="4e32e-150">弱型別 （或在 OUT） REF CURSOR 參數都由泛型記錄類別。</span><span class="sxs-lookup"><span data-stu-id="4e32e-150">Weakly-typed OUT (or IN OUT) REF CURSOR parameters are represented by the generic record class.</span></span> <span data-ttu-id="4e32e-151">一般的資料錄集時，一定會產生相同的命名空間，並使用相同的類別名稱，不論函式或程序。</span><span class="sxs-lookup"><span data-stu-id="4e32e-151">The generic record set is always generated in the same namespace and with the same class name regardless of the function or procedure.</span></span> <span data-ttu-id="4e32e-152">下列程式碼將示範一般記錄類別， **microsoft.lobservices.oracledb._2007._03.GenRecordRow**，用來表示 OUTRECS 出 SYS_REFCURSOR 參數 （弱型別） 的記錄。</span><span class="sxs-lookup"><span data-stu-id="4e32e-152">The following code shows the generic record class, **microsoft.lobservices.oracledb._2007._03.GenRecordRow**, which represents the records for the OUTRECS OUT SYS_REFCURSOR parameter (weakly-typed).</span></span>  
  
```  
namespace microsoft.lobservices.oracledb._2007._03 {  
    using System.Runtime.Serialization;  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordRow : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumnField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute()]  
        public microsoft.lobservices.oracledb._2007._03.GenRecordColumn[] GenRecordColumn {  
            get {  
                return this.GenRecordColumnField;  
            }  
            set {  
                this.GenRecordColumnField = value;  
            }  
        }  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute()]  
    public partial class GenRecordColumn : object, System.Runtime.Serialization.IExtensibleDataObject {  
  
        private System.Runtime.Serialization.ExtensionDataObject extensionDataField;  
  
        private string ColumnNameField;  
  
        private string ColumnValueField;  
  
        private string ColumnTypeField;  
  
        public System.Runtime.Serialization.ExtensionDataObject ExtensionData {  
            get {  
                return this.extensionDataField;  
            }  
            set {  
                this.extensionDataField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false)]  
        public string ColumnName {  
            get {  
                return this.ColumnNameField;  
            }  
            set {  
                this.ColumnNameField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true)]  
        public string ColumnValue {  
            get {  
                return this.ColumnValueField;  
            }  
            set {  
                this.ColumnValueField = value;  
            }  
        }  
  
        [System.Runtime.Serialization.DataMemberAttribute(IsRequired=true, EmitDefaultValue=false, Order=2)]  
        public string ColumnType {  
            get {  
                return this.ColumnTypeField;  
            }  
            set {  
                this.ColumnTypeField = value;  
            }  
        }  
    }  
}  
```  
  
## <a name="using-ref-cursor-parameters-with-a-wcf-client"></a><span data-ttu-id="4e32e-153">使用 WCF 用戶端使用 REF CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="4e32e-153">Using REF CURSOR Parameters with a WCF Client</span></span>  
 <span data-ttu-id="4e32e-154">要叫用程序或函式的 REF CURSOR 參數，使用 WCF 用戶端，您執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="4e32e-154">To invoke a procedure or function with REF CURSOR parameters by using a WCF client, you do the following:</span></span>  
  
1.  <span data-ttu-id="4e32e-155">將字串傳遞中的 for each 或 IN OUT REF CURSOR 參數包含 PL/SQL 封鎖開啟 REF CURSOR。</span><span class="sxs-lookup"><span data-stu-id="4e32e-155">Pass a string for each IN or IN OUT REF CURSOR parameter that contains the PL/SQL block to open the REF CURSOR.</span></span> <span data-ttu-id="4e32e-156">這個區塊可以執行為開啟的 SELECT 陳述式或叫用函式或 OUT 參數中傳回開啟的 REF CURSOR 的程序。</span><span class="sxs-lookup"><span data-stu-id="4e32e-156">This block can either execute an OPEN FOR SELECT statement or invoke a function or procedure that returns an opened REF CURSOR in an OUT parameter.</span></span>  
  
2.  <span data-ttu-id="4e32e-157">當程序或函式傳回時，作業傳回的任何 OUT 或 IN OUT REF CURSOR 參數的記錄組中的資料。</span><span class="sxs-lookup"><span data-stu-id="4e32e-157">When the procedure or function returns, operate on the data in the record sets returned for any OUT or IN OUT REF CURSOR parameters.</span></span> <span data-ttu-id="4e32e-158">資料錄集將會設定弱式類型的 REF CURSOR 參數的泛型記錄或設定強型別 REF CURSOR 參數的強型別記錄。</span><span class="sxs-lookup"><span data-stu-id="4e32e-158">The record set will be a generic record set for weakly-typed REF CURSOR parameters or a strongly-typed record set for strongly-typed REF CURSOR parameters.</span></span>  
  
 <span data-ttu-id="4e32e-159">如需如何使用 WCF 服務模型叫用程序和函數的詳細資訊，請參閱[叫用函式和 Oracle 資料庫使用 WCF 服務模型中的程序](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md)。</span><span class="sxs-lookup"><span data-stu-id="4e32e-159">For more information about how to invoke procedures and functions by using the WCF service model, see [Invoke Functions and Procedures in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
 <span data-ttu-id="4e32e-160">下列範例會呼叫 GET_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="4e32e-160">The following example calls the GET_ACTIVITY procedure.</span></span> <span data-ttu-id="4e32e-161">它會示範指定中 REF CURSOR 參數的兩個方法：</span><span class="sxs-lookup"><span data-stu-id="4e32e-161">It demonstrates both ways of specifying an IN REF CURSOR parameter:</span></span>  
  
-   <span data-ttu-id="4e32e-162">為開啟的 SELECT 陳述式中 REF CURSOR 參數被指定要針對帳戶 100001 傳回活動。</span><span class="sxs-lookup"><span data-stu-id="4e32e-162">For the IN REF CURSOR parameter, an OPEN FOR SELECT statement is specified to return activity for ACCOUNT 100001.</span></span>  
  
-   <span data-ttu-id="4e32e-163">在出 REF CURSOR 參數，會叫用 /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY 程序。</span><span class="sxs-lookup"><span data-stu-id="4e32e-163">For the IN OUT REF CURSOR parameter, the /SCOTT/Package/ACCOUNT_PKG/GET_ALL_ACTIVITY procedure is invoked.</span></span> <span data-ttu-id="4e32e-164">此程序會開啟 REF 資料指標，其中包含所有 ACCOUNTACTIVITY 資料表中的活動，並傳回做為 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="4e32e-164">This procedure opens a REF CURSOR that contains all of the activity in the ACCOUNTACTIVITY table and returns it as an OUT parameter.</span></span>  
  
 <span data-ttu-id="4e32e-165">此範例也示範如何讀取記錄集傳回強型別與弱式類型的 REF CURSOR 參數的資料。</span><span class="sxs-lookup"><span data-stu-id="4e32e-165">The example also demonstrates how to read data from the record set returned for both strongly-typed and weakly-typed REF CURSOR parameters.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Include this namespace for WCF LOB Adapter SDK and Oracle Database adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// namespaces for strongly-typed and weakly typed REF CURSOR records  
using GET_ACTIVITYns = microsoft.lobservices.oracledb._2007._03.SCOTT.Package.ACCOUNT_PKG.GET_ACTIVITY;  
using GENERICns = microsoft.lobservices.oracledb._2007._03;  
  
// In this sample, INRECS is opened by using an OPEN FOR statement, and  
// INOUTRECS_IN is opened by calling the GET_ALL_ACTIVITY procedure on Oracle.  
  
namespace OracleRefCursorsSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Create the client  
            SCOTTPackageACCOUNT_PKGClient accountPkgClient =   
                new SCOTTPackageACCOUNT_PKGClient("OracleDBBinding_SCOTT.Package.ACCOUNT_PKG");  
            // Set credentials  
            accountPkgClient.ClientCredentials.UserName.UserName = "SCOTT";  
            accountPkgClient.ClientCredentials.UserName.Password = "TIGER";  
  
            try  
            {  
  
                GET_ACTIVITYns.INOUTRECSRECORD[] strongCursor;  
                GENERICns.GenRecordRow[] weakCursor;  
  
                Console.WriteLine("Opening client");  
                // Open the client  
                accountPkgClient.Open();  
  
                Console.WriteLine("Invoking ACCOUNT_PKG.GET_ACTIVITY");  
                // Get  ACCOUNTACTIVITY records  
                // The IN REF CURSOR is set to all activity for account 100001  
                // The input part of the IN OUT ref cursor calls GET_ALL_ACTIVITY  
                // The weakly-typed OUT REF CURSOR parameter returns a list of activity for account 100001  
                // The strongly-typed IN OUT REF CURSOR parameter returns a list of all activity  
                string inRecsString = "BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;";  
                string inoutRecsString = "BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;";  
  
                accountPkgClient.GET_ACTIVITY(  
                                inRecsString,  
                                inoutRecsString,  
                                out strongCursor,  
                                out weakCursor);  
  
                // Display strong ref cursor (all activity)  
                Console.WriteLine("\nList of all activity returned (strong ref cursor)");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < strongCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2:C}\t{3}\t{4}",strongCursor[i].TID,  
                        strongCursor[i].ACCOUNT,   
                        strongCursor[i].AMOUNT,   
                        strongCursor[1].TRANSDATE,  
                        strongCursor[i].DESCRIPTION);  
                }  
  
                // Display weak ref cursor (account 100001)  
                Console.WriteLine("\nList of activity for account 100001 returned (weak ref cursor)");  
                Console.WriteLine("Tx Id\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < weakCursor.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1:C}\t{2}\t{3}", weakCursor[i].GenRecordColumn[0].ColumnValue,  
                        weakCursor[i].GenRecordColumn[2].ColumnValue,  
                        weakCursor[i].GenRecordColumn[4].ColumnValue,  
                        weakCursor[i].GenRecordColumn[3].ColumnValue);  
                }  
  
                Console.WriteLine("\nHit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
                throw ex;  
            }  
            finally  
            {  
                // Close the client  
                accountPkgClient.Close();  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e32e-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e32e-166">See Also</span></span>  
 [<span data-ttu-id="4e32e-167">開發 Oracle 資料庫應用程式使用 WCF 服務模型</span><span class="sxs-lookup"><span data-stu-id="4e32e-167">Develop Oracle Database Application Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)