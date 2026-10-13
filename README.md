# clone-lin-gmx-v2-impact-delta

Experimental LIN clone of GMX V2 `applyDeltaToPositionImpactPool` (uint64-scale signed pool + lent pairing).

- **Upstream:** [gmx-io/gmx-synthetics](https://github.com/gmx-io/gmx-synthetics) `contracts/market/MarketUtils.sol` commit `a85ea3491c19c93bb4b5a002d9b358fb769b7849` (GPL-2.0-or-later after BUSL Change Date 2026-08-31).
- **LIN kernel:** [`src/lin_gmx_v2_impact_delta.lin`](src/lin_gmx_v2_impact_delta.lin)
- **Proofs (lin-open only):** [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open) `examples/gmx_v2_impact_delta/` and `python3 test/prove_gmx_v2_impact_delta_external.py`
- **Class:** EXPERIMENTAL. Not Arbitrum GMX V2 uint256. Not a production replacement. Not `capPositiveImpactUsdByPositionImpactPool` (USD clip) and not `applyBoundedDeltaToUint` (swap floor-at-zero).

Named goldens (uint64-scale, pool=1e8 lent=2e7): negative-within pool **70000000** / lent **20000000**; negative-excess pool **0** / lent **70000000** vs naive **-50000000** vs swap-floor lent **20000000**; positive-within pool **100000000** / lent **10000000**; positive-excess pool **130000000** / lent **0** vs naive **150000000** vs repay-only **100000000** vs abs-draw **50000000**; 7e18+3e18 fail-closes vs naive i64 wrap **-8446744073709551616**.
